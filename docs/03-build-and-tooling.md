# Build and tooling

## Install options (users)

From upstream English docs (`getting-started/install.md`) and README:

1. **Recommended:** VS Code + [rzk extension](https://marketplace.visualstudio.com/items?itemName=NikolaiKudasovfizruk.rzk-1-experimental-highlighting) (can prompt to install `rzk` binaries).
2. **GitHub Releases:** platform binaries at `https://github.com/rzk-lang/rzk/releases` (latest surveyed: **v0.11.3**, 2026-08-31).
3. **Hackage (stable):**
   ```sh
   cabal update
   cabal install rzk
   # or
   stack install rzk
   ```
4. **From `develop`:**
   ```sh
   git clone https://github.com/rzk-lang/rzk.git
   cd rzk && git checkout develop
   stack build && stack install
   # or cabal v2-build && cabal v2-install
   ```

Verify: `rzk version` (tools parse bare stdout); `rzk version --full` for commit/compiler/platform/LSP flags.

## Developer builds

### Stack

- `stack.yaml`: resolver **lts-24.34**, package `rzk`, extra-deps `free-foil-0.4.0`, `kind-generics-th-0.2.3.3`
- Typical loop: `stack build`, `stack exec -- rzk typecheck FILE`, `stack test`

### Cabal

- `cabal.project`: packages `rzk` and `rzk-js`; `write-ghc-environment-files: always` (doctest-parallel); **constraints** block floors aeson≥2, base≥4.19, etc. for GHC 9.8-era coherence without breaking the older GHCJS/Nix package set (cabal2nix ignores `cabal.project` constraints)

### Nix / flakes

- `flake.nix`, `default.nix`, `shell.nix`, `nix/` helpers, `.envrc` for direnv
- Cachix hint: `miso-haskell` (README) for JS-related caches
- Dev shells expose `cabal`, GHC, HLS, hpack; separate shells for GHCJS / playground release
- Incremental day-to-day builds: prefer **cabal inside nix develop**; pure `nix build` rebuilds more aggressively

### Parser regeneration

```sh
cabal install BNFC-2.9.6.3 happy-2.2 alex   # version-sensitive
make -C rzk regen-parser
```

## Everyday checker commands

```sh
# Single or ordered multi-file
rzk typecheck first.rzk.md second.rzk.md

# Glob with numeric prefixes (recommended until real deps exist)
rzk typecheck *-*.md

# Holes (games / partial proofs)
rzk typecheck --allow-holes draft.rzk.md

# Machine-readable diagnostics
rzk typecheck --json file.rzk.md

# Format
rzk format --write '**/*.rzk.md'
rzk format --check   # non-zero if dirty; uses rzk.yaml when no paths
```

Literate style: Markdown with fenced `rzk` blocks and `#lang rzk-1`.

## `rzk.yaml`

Minimal schema (`Rzk.Project.Config`):

```yaml
include:
  - docs/docs/en/getting-started/dependent-types.rzk.md
exclude: []
```

Used when `format` (and related path expansion) is invoked without explicit files. Project template: [rzk-lang/rzk-project-template](https://github.com/rzk-lang/rzk-project-template).

## Tests

- **`rzk-test`:** hspec; golden cases under `rzk/test/typecheck/cases/` with `SCHEMA.md` and `*.expect.yaml`
- **`doctests`:** `doctest-parallel`
- LSP-related specs gated on `LSP_ENABLED`

## CI workflows (`.github/workflows/`)

| Workflow | Purpose |
|----------|---------|
| `ghc.yml` | Build/test/haddock; MkDocs deploy; matrix OS (ubuntu/windows/macos); pushes to `main`/`develop` and tags `v*` |
| `cabal.yml` | Cabal pathway / bounds hygiene |
| `parser-drift.yml` | Regen parser vs committed sources |
| `playground.yml` | Playground build/deploy |
| `wasm.yml` | WASM build path |
| `release.yml` | On published GitHub Release: Hackage *candidate* upload + multi-OS binaries |
| `bench.yml` | Benchmarks (`bench/`) |
| `cache-cleanup.yml` | CI cache maintenance |

Release automation uploads a Hackage **candidate** (`publish: false` in `haskell-actions/hackage-publish`) and attaches binaries—human publish step remains on Hackage.

## Related automation for *users* of Rzk

- GitHub Action: [rzk-lang/rzk-action](https://github.com/rzk-lang/rzk-action) — typecheck (and experimental format check) on formalization repos
- MkDocs plugin: [rzk-lang/mkdocs-plugin-rzk](https://github.com/rzk-lang/mkdocs-plugin-rzk) — anchors, experimental diagram rendering for literate files
