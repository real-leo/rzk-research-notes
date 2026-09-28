# Overview: what Rzk is

## One-sentence summary

**Rzk** is an experimental proof assistant that implements (a practical fragment of) Riehl and Shulman’s *type theory with shapes*—a three-layered dependent type theory designed for **synthetic (∞,1)-category theory** inside a homotopy-type-theoretic setting.

## Problem domain

Ordinary homotopy type theory (HoTT) is often described as a synthetic theory of ∞-groupoids: every type carries higher identity structure automatically. Synthetic ∞-*categories* need an additional **directed** dimension. Riehl–Shulman’s approach does not replace HoTT with a fully directed type theory. Instead it:

1. Works in a setting whose intended semantics include **bisimplicial sets** (simplicial spaces), where one direction is “spatial” (homotopy) and one is “categorical” (directed).
2. Adds a **directed interval** (cube) and a coherent **tope** logic for shapes inside cubes.
3. Uses **extension types** so that “arrows from *x* to *y*” can be functions on the interval with *strict* endpoint constraints—without dragging propositional equalities through every definition.
4. Isolates **Segal types** and **Rezk types** as the objects that behave like (flagged) (∞,1)-categories.

Rzk’s job is to make that paper language executable: parse `rzk-1`, check definitions against the cube / tope / type layers, solve tope obligations with a built-in solver, and support literate Markdown projects used by working mathematicians.

## Status and maturity

| Aspect | Assessment |
|--------|------------|
| Self-description | “Experimental” (README, MkDocs, Hackage synopsis) |
| Version at survey | **0.11.3** (2026-08-31); active `develop` branch |
| Soundness posture | Assumes **type-in-type** (`U : U`); cube/tope may depend on types more liberally than a carefully stratified theory—accepted for now as simplifying and “good enough” for target formalizations |
| Scale of use | Multi-file libraries exist: **sHoTT** (simplicial HoTT / ∞-categories) and **yoneda** (comparative Yoneda formalizations); enough to stress GC and conversion (sHoTT checking is a standard perf corpus in `package.yaml` comments) |
| Tooling | CLI typecheck/format, optional **LSP**, VS Code extension, browser **playground** (WASM/JS), interactive **games**, GitHub Action, MkDocs plugin |
| Team size | Small core (see `CONTRIBUTORS.md`); Zulip community |

Rzk is mature enough to check substantial synthetic ∞-category developments and to ship binary releases and Hackage packages, but it is **not** a general-purpose replacement for Agda/Cubical Agda, Coq-HoTT, or Lean. Its niche is precisely RSTT-style synthetic directed HoTT, with an emphasis on keeping the *core* small via second-order abstract syntax / free-foil and (planned) E-unification libraries.

## What Rzk is *not*

- Not a tactic-heavy prover in the Lean/Coq style: proofs are mostly direct terms (`#define`, path induction `idJ`, extension types, tope reasoning mostly automatic).
- Not a full cubical type theory à la Cubical Agda (though it has a Dedekind interval cube `𝕀` / `II` alongside the directed interval `2`).
- Not finished on multi-file dependency management: file order is still largely a user responsibility (see [05-limitations-and-roadmap.md](05-limitations-and-roadmap.md)).

## Primary entry points

- Upstream README: `https://github.com/rzk-lang/rzk/blob/develop/README.md`
- English MkDocs: `https://rzk-lang.github.io/rzk/`
- Playground (develop): `https://rzk-lang.github.io/rzk/develop/playground/`
- Paper: Riehl–Shulman 2017, [arXiv:1705.07442](https://arxiv.org/abs/1705.07442)
