# Limitations and roadmap

Rzk is explicit about being **experimental**. The points below are drawn from upstream docs, README “future” statements, ChangeLog themes, and code comments—not from private roadmaps.

## Current limitations

### Foundational / soundness

- **Type-in-type:** `U : U` is assumed. This is known to be inconsistent in general (Girard’s paradox family) but is a common pragmatic choice in experimental assistants; Rzk documents it under “Soundness” in `reference/introduction.rzk.md`.
- **Layer stratification is lax:** cubes/topes may depend on types/terms in ways a carefully stratified RSTT presentation might forbid. Upstream judges this unlikely to spoil “proofs of interest” today, but it is a consistency risk and a future cleanup item.

### Language and checker

- **Multi-file dependencies:** There is no real import graph yet. `rzk typecheck` takes an **ordered** list of files; later files see earlier definitions. Recommended workaround: numeric prefixes + globs (`rzk typecheck *-*.md`). Proper inter-file dependencies are stated as future work (README).
- **Tope solver scope:** Sufficient for existing synthetic ∞-category formalizations, but not a fully extensible geometric HoTT toolkit. User-defined cubes/axioms live in **simple-topes** first.
- **Inference:** Dependent type inference via **E-unification for second-order abstract syntax** is a stated aim ([arXiv:2302.05815](https://arxiv.org/abs/2302.05815)), not the default everyday experience of a fully inferencing assistant like Lean.
- **Modalities:** Experimental since v0.8; syntax and mode theory may change (`reference/modalities.rzk.md`).
- **Formatter:** Useful and CI-checkable, but still described as experimental in places; style follows yoneda/sHoTT / agda-unimath conventions.

### Architecture debt

- **Dual term representations:** free-foil AST exists and builds, but the checker has not fully cut over (`Language.Rzk.Foil.Syntax` comments). Until swap-over completes, contributor mental load stays higher.
- **Parser toolchain:** Out-of-band BNFC regeneration is intentional (WASM/Hackage), but grammar edits need discipline + drift CI.
- **Documentation gaps:** e.g. `getting-started/project.md` still “work-in-progress” (points at the project template); Nix install section in install.md similarly incomplete in places.

### Product / ecosystem

- Small maintainer set relative to Agda/Coq/Lean.
- VS Code is the first-class editor path; other editors must wire LSP themselves.
- Not all platforms may have release binaries every time—users are invited to file issues.

## Roadmap themes (public signals)

| Theme | Evidence | Intended payoff |
|-------|----------|-----------------|
| **E-unification / dependent inference “as a library”** | README; FSCD 2023 paper; free-foil investment | Smaller, safer core; less manual annotation |
| **Finish free-foil cutover** | Foil module docs; ongoing PRs in ChangeLog | One binder story; perf (0.4.0 already helped sHoTT) |
| **Merge simple-topes** | README | Type theory with shapes beyond fixed RSTT builtins—cubical/globular/… variants |
| **Real multi-file projects** | README explicit future | Libraries without fragile ordering |
| **Modal / TTT maturation** | modalities docs; sHoTT `diruniv` | Directed univalence and modal synthetic methods |
| **Tooling polish** | LSP features, hole suggestions, JSON diagnostics, games | Lower barrier for mathematicians |

## What “done enough” already looks like

Despite the above, Rzk already:

- Checks large RSTT-style developments (yoneda geodesic, sHoTT corpus).
- Ships versioned binaries + Hackage + playground + teaching games.
- Automates tope obligations that would otherwise dominate proof scripts.

Treat limitations as **scope boundaries**, not as signs the tool is unusable for its niche.
