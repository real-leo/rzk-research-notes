# Type theory background (Riehl–Shulman)

This note summarizes the mathematical setting that Rzk implements, citing Emily Riehl & Michael Shulman, *A type theory for synthetic ∞-categories*, Higher Structures 1(1), 147–224, 2017 ([arXiv:1705.07442](https://arxiv.org/abs/1705.07442)). Rzk’s surface language `rzk-1` tracks the paper’s three layers closely (see upstream `docs/docs/en/reference/`).

## Motivation (from the paper’s abstract)

The paper proposes foundations for a **synthetic theory of (∞,1)-categories** inside homotopy type theory. The authors:

- Axiomatize a **directed interval** type.
- Build higher simplices from it and use them to probe internal categorical structure of arbitrary types.
- Define **Segal types** (unique composites up to homotopy → coherent associativity/unitality).
- Define **Rezk types** (categorical isomorphisms coincide with identity types—“local univalence”).
- Define **covariant fibrations** and prove a **dependent Yoneda lemma** (directed analogue of identity elimination).
- Study adjunctions between Segal/Rezk types.

Bookkeeping uses a **three-layered type theory with shapes**: cube contexts, tope logic for polytopes in cubes, and ordinary HoTT types over those contexts, with **extension types** generalizing path-types of cubical TT.

Intended semantics (appendix of the paper): Reedy model structure on **bisimplicial sets**; Segal/Rezk types correspond to Segal spaces / complete Segal spaces.

## Three layers

Rzk exposes three universes matching the paper (upstream introduction):

| Layer | Universe in `rzk-1` | Role |
|-------|---------------------|------|
| Cubes | `CUBE` | Directed (and cubical) intervals and their products—“shapes’ ambient space” |
| Topes | `TOPE` | Coherent logic of subshapes (conjunction, disjunction, equality/inequality of points)—no classical negation |
| Types | `U` | Ordinary dependent types / terms; Segal/Rezk structure lives here |

### Cube layer (shapes’ geometry)

Built-in cubes in Rzk (docs `reference/cube-layer.rzk.md`):

- `1` — unit cube, point `*_1`
- `2` — **directed interval** with endpoints `0_2`, `1_2` and order `<=` (the paper’s \(\mathbb{2}\))
- `𝕀` / `II` — Dedekind **cubical** interval (no total order); `2` is a subtype of `𝕀`

Products: `I × J`, pairing `(t, s)`, projections `first` / `second`. Lattice operations `⊔`/`⊓` (ASCII `sup`/`inf`) on interval cubes.

Simplices are *shapes*: cubes restricted by topes, e.g. \(\Delta^2 = \{(t_1,t_2) \mid t_2 \le t_1\}\). Rzk users typically write shape restrictions in binders rather than constructing \(\Delta^n\) as first-class named types.

### Tope layer (shape logic)

Topes (`TOPE`) describe which points of a cube are “in” a shape. Connectives (docs `reference/tope-layer.rzk.md`):

- `TOP`, `BOT`
- `psi /\ phi`, `psi \/ phi`
- Point equality `t === s`
- Inequality on the directed interval `t <= s`

An important design point from the paper and from Rzk’s implementation: **tope entailments are solved automatically** by a dedicated solver (intuitionistic theorem prover for this fragment). Users rarely write explicit tope proofs; the checker asks whether a tope follows from assumptions when checking extension types and shape-restricted Πs. A standalone experiment for a more general solver is [fizruk/simple-topes](https://github.com/fizruk/simple-topes).

### Type layer and extension types

Ordinary MLTT-style constructs exist: dependent products `(x : A) -> B`, Σ-types `Σ (x : A), B`, identity types `x = y` with `refl` and `idJ`, `let`, etc. (`reference/type-layer.rzk.md`).

The directed hallmark is the **extension type** (paper §2.2; Rzk `reference/extension-types.rzk.md`):

```text
(t : I | psi t) -> A [ phi |-> a ]
```

Informally: dependent functions on the shape `{t : I | psi}` that **judgmentally** restrict to a given section `a` on a cofibrant subshape `{t : I | phi}`. Special cases:

- Shape-restricted function types `(t : I | psi t) -> A` (extension along `BOT`).
- Hom-types in the paper: arrows from `x` to `y` as extensions of the boundary inclusion \(\partial\Delta^1 \hookrightarrow \Delta^1\).

This avoids encoding endpoint conditions as propositional equalities packaged in Σ-types—critical for readable 2- and 3-simplex bookkeeping.

## Segal and Rezk types (conceptual)

- **Segal type:** composable arrows have a contractible space of composites (internally often stated at dimension 2, with higher coherences following in the synthetic setting).
- **Rezk type:** Segal + completeness (isomorphisms ≃ identities).

Rzk’s large libraries formalize ∞-categorical material (Yoneda, etc.) in this language; see [arxiv:2309.08340](https://arxiv.org/abs/2309.08340) (*Formalizing the ∞-categorical Yoneda lemma*, Kudasov–Riehl–Weinberger).

## Modalities (experimental, post-paper)

From Rzk v0.8, an experimental **modal extension** supports Triangulated Type Theory–style modalities (`♭` / `_b`, `♯` / `_#`, `ᵒᵖ` / `_op`) with a parameterized mode theory (docs `reference/modalities.rzk.md`; work by Islam Talipov). This is beyond the 2017 paper and remains unstable in surface syntax.

## Design tradeoff vs “native” directed TT

Riehl–Shulman (and thus Rzk) accept **extra non-Segal types** in the universe: not every type is a category. The payoff is a full HoTT toolkit (Π, Σ, universes, function extensionality-style axioms for extensions) while still carving out synthetic (∞,1)-categories. A “pure” directed type theory might avoid junk types but historically struggles with exponentiability, fibration variance, and coherence boilerplate—exactly the problems the paper’s indirect route sidesteps.
