# Architecture

Survey based on the `rzk-lang/rzk` monorepo (`develop` tip, package version **0.11.3**). Paths below are relative to the repository root.

## Monorepo layout

```text
rzk/                     # Haskell package (library + `rzk` executable)
  app/Main.hs            # CLI entry
  grammar/Syntax.cf      # BNFC grammar (source of truth for syntax)
  src/
    Language/Rzk/Syntax/ # Committed BNFC/alex/happy output
    Language/Rzk/Foil/   # free-foil AST (migration in progress)
    Language/Rzk/VSCode/ # LSP (cabal flag `lsp`, not on GHCJS)
    Rzk/TypeCheck/       # Split typechecker (~8–10k lines across modules)
    Rzk/Format.hs, Project/, Diagnostic.hs, ...
  test/                  # hspec + golden typecheck cases + doctests
rzk-js/                  # JS/WASM wrapper used by the playground
rzk-playground/          # Vite/TS editor UI + Lezer grammar
docs/                    # MkDocs site (en/ + ru/)
nix/, flake.nix          # Nix / flakes toolchain
.github/workflows/       # GHC, Cabal, parser-drift, playground, wasm, release, bench
rzk.yaml                 # Default include list for format/typecheck helpers
stack.yaml, cabal.project
```

**Default git branch:** `develop` (releases tagged `v*`; `main` also receives CI).

## CLI surface

Executable name: `rzk` (`rzk/app/Main.hs`, `optparse-generic`).

| Command | Role |
|---------|------|
| `rzk typecheck [FILE...]` | Parse and typecheck modules (stdin if no files). Flags: `--allow-holes` / `-H`, `--json` / `-j` |
| `rzk format [FILE...]` | Format to stdout; `--write` / `-w` overwrite; `--check` / `-c` CI mode. Empty file list → paths from `rzk.yaml` |
| `rzk lsp` | Language server (`LSP_ENABLED` builds only) |
| `rzk version` | Bare version string by default; `--full` / `-f`, `--json` / `-j` |

RTS tuning is intentional: `package.yaml` sets `-with-rtsopts=-N -A64m` because checking sHoTT is nursery/GC-bound (comments cite ~5.0s → ~2.2s with a 64 MB nursery).

See [appendix-cli-reference.md](appendix-cli-reference.md).

## Typechecker pipeline (conceptual)

1. **Parse** literate Markdown or `.rzk` via BNFC-generated `Language.Rzk.Syntax` (layout handling in `Syntax/Layout.hs`).
2. **Elaborate / check** declarations (`#define`, `#def`, `#postulate`, `#data`, `#compute`, `#check`, options, sections, …) under cube/tope/type contexts.
3. **Evaluate / convert** terms (`Rzk.TypeCheck.Eval`, `NbE`, `Unify`) with a conversion fast path (v0.11.x: spine-to-spine comparison for stuck apps, inspired by Kovács’ smalltt—see ChangeLog).
4. **Solve topes** inside judgments that require shape inclusions or extension-type side conditions.
5. **Report** diagnostics (`Rzk.Diagnostic`); holes can be allowed for games / interactive UX.

Public re-export module: `Rzk.TypeCheck` (formerly one huge module; now layered: `Judgements`, `Decl`, `Context`, `Monad`, `Error`, …). Rough scale at survey: on the order of **10k+ lines** under `Rzk/TypeCheck/` plus Foil modules.

## free-foil and binders

Rzk’s long-term strategy is **second-order abstract syntax** so binders are less error-prone and higher-order unification / dependent inference can be library-shaped (README; papers arXiv:2204.05653, arXiv:2302.05815).

Dependency: **`free-foil` ≥ 0.4** ([fizruk/free-foil](https://github.com/fizruk/free-foil)) — “Efficient Type-Safe Capture-Avoiding Substitution for Free (Scoped Monads).”

Important nuance from `Language/Rzk/Foil/Syntax.hs` module docs:

> The free-foil AST is the **successor** of an older `Language.Rzk.Free.Syntax` representation. It is **compiled but not yet fully consumed**: the checker still largely runs on the old representation; swap-over is staged.

So architecture is mid-migration: new Foil syntax + convert/print modules exist (`Foil/Convert.hs`, `Print.hs`, `Names.hs`), while production checking remains tied to the legacy term representation until the cutover finishes. `stack.yaml` pins `free-foil-0.4.0` as an `extra-dep` for ZipMatchK / O(1) sink features the core needs.

## Parser / BNFC

- Grammar: `rzk/grammar/Syntax.cf`
- Tools: BNFC + alex + happy; regenerate with `make -C rzk regen-parser`
- **Committed** generated Haskell under `rzk/src/Language/Rzk/Syntax/`
- `build-type: Simple` (no Custom `Setup.hs`) so Hackage installs stay light and the **GHC WASM** backend can build (Custom Setup cannot run under wasm)
- CI workflow `parser-drift.yml` regenerates and fails on drift
- Pinned tool versions matter (README: BNFC `2.9.6.3`, happy `2.2`)

## LSP and editor integration

Cabal flag `lsp` (default true, disabled for GHCJS):

- Modules under `Language.Rzk.VSCode.*` (Config, Env, Handlers, Lsp, Tokenize, ReferenceIndex, …)
- Depends on `lsp` / `lsp-types` 2.x
- VS Code extension: [rzk-lang/vscode-rzk](https://github.com/rzk-lang/vscode-rzk) (Marketplace id `NikolaiKudasovfizruk.rzk-1-experimental-highlighting`)

## Playground / WASM / JS

- `rzk-js`: wraps the checker for browser use; historically GHCJS via Nix; also WASM workflow (`wasm.yml`)
- `rzk-playground`: TypeScript + Vite UI, Lezer grammar (`rzk-lezer`), loads compiled checker JS
- Deployed under GitHub Pages paths such as `/rzk/latest/playground/` and `/rzk/develop/playground/`

Games ([rzk-lang/rzk-game](https://github.com/rzk-lang/rzk-game)) similarly embed the typechecker in-browser (hole filling with goals/contexts)—a different product surface on the same core.

## Project configuration

`Rzk.Project.Config` parses YAML:

```yaml
include:
  - path/to/file.rzk.md
exclude: []   # optional
```

Root `rzk.yaml` in upstream lists a couple of doc examples. Multi-file **dependency resolution is still order-based**: `rzk typecheck a b c` checks in the given order; wildcards + numeric prefixes are the recommended convention until real imports land.

## Design tradeoffs (architecture)

| Choice | Benefit | Cost |
|--------|---------|------|
| Commit generated parser | Easy Hackage + WASM | Manual regen + drift CI |
| free-foil migration | Safer binders, future E-unification | Dual representations for a while |
| Large RTS nursery | Fast library checks | Higher default memory footprint |
| Optional LSP flag | Smaller JS builds | Feature matrix across backends |
| Tope solver in-core | No tope proof burden for users | Solver completeness/generality limits (hence simple-topes) |
