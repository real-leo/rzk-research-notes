# Metatheory and semantics (RSTT ↔ Rzk)

Technical takeaways from the **system paper** Kudasov–Sim–Ahrens, *Rzk: a Proof Assistant for Synthetic ∞-Categories* ([arXiv:2607.12207](https://arxiv.org/abs/2607.12207)), grounded in Riehl–Shulman RSTT ([arXiv:1705.07442](https://arxiv.org/abs/1705.07442)). Paraphrase only; see PDFs for proofs.

**Status labels.** *Verified* = claim appears in the cited abstract/intro/body as read 2026-09-28. *Open in literature* = stated as conjecture / future work in those papers.

---

## 1. Three objects to keep distinct

| Object | Role |
|--------|------|
| **MPL + RSTT** | Paper type theory of shapes + meta-theoretic parameter layer formalising schematic cube/tope/family assumptions |
| **Declarative Rzk (dRzk)** | RSTT + **split extension types** + **coercion-free subtyping** |
| **Algorithmic Rzk (aRzk)** | dRzk + **first-class parameters**, **bidirectional checking**, **automated tope solver** — what the Haskell checker implements |

The system paper’s slogan (intro): Rzk is roughly RSTT plus those declarative refinements, plus the algorithmisation that makes checking practical.

---

## 2. Deeper RSTT: shapes, tope logic, extension types

From [arXiv:1705.07442](https://arxiv.org/abs/1705.07442) and the system paper’s §3 review (*verified*):

### Cubes

Simply-typed geometry: unit cube `𝟙`, directed interval `𝟚` with endpoints `0`, `1`, products `I × J`. Cube contexts bind points of cubes. In paper RSTT, **abstract cubes are meta-level** (not bound in object contexts).

### Topes

Intuitionistic propositional logic over cubes: `⊤`, `⊥`, `∧`, `∨`, point equality `s ≡ t`, interval order `s ≤ t`. **No** implication or classical negation in the coherent fragment used for shapes. Entailments `Ξ | Φ ⊢ ψ` are side conditions, often left implicit on paper.

Interval axioms (total order, `0` least / `1` greatest, endpoints distinct) carve simplices as shapes, e.g.

- `Δ¹ = {t : 𝟚 | ⊤}`
- `Δ² = {(t,s) : 𝟚×𝟚 | s ≤ t}`
- `Λ²₁ = {(t,s) | (s ≡ 0) ∨ (t ≡ 1)}`

### Extension types

Given shape `{t:I | ψ}`, subshape `{t:I | φ}` with `φ ⊢ ψ`, family `A` over the shape, and section `a` over the subshape, the extension type is the type of sections over the whole shape that **definitionally** agree with `a` on `φ`. Hom-types are the leading example: maps out of `Δ¹` with endpoints pinned by `rec_∨`.

Semantic motivation (paper appendix / intro): Reedy model structure on **bisimplicial sets**; Segal / Rezk types ↔ Segal / complete Segal spaces. Broader: simplicial objects in ∞-toposes (Shulman; Weinberger) — see also [01-type-theory-background.md](01-type-theory-background.md).

---

## 3. Declarative refinements in Rzk

### Split extension types (*verified*, §4.2)

dRzk factors RSTT’s fused former into:

1. **Shape-indexed Π** — `Π_{t:{I|ψ}} B` (empty-boundary case made primitive).
2. **Type restriction** — `B [φ ↦ a]` attaching a definitional boundary to *any* type.

Motivation: type checking produces **intermediate** types (e.g. applying a hom at a point) that keep a restriction on the *codomain* after consuming the shape-Π — a type RSTT’s fused former cannot name. Surface multi-branch restrictions desugar via tope `∨`-elimination.

### Coercion-free subtyping (*verified*, §4.3)

Paper proofs silently re-read restricted sections as plain functions (η / notational blur). dRzk adds `A <: B` with **subsumption that does not change the term** (no inserted coercions). Selected rules: drop restriction (`S-Restr′`), weaken/restrict boundaries, shape-Π variance, split over entailed `∨`.

**Caveat (*verified*, Remark on η):** some RSTT passages (e.g. forward map in cofibration composition) are sound only for a **particular** section, not for all inhabitants of its type — hence not subtyping. dRzk requires η-expanded witnesses there; typing is **not** invariant under η-contraction of subjects. Pointwise subsumption is prototyped but **not** in the paper’s declarative theory.

---

## 4. Meta-theoretic parameter layer (MPL)

Riehl–Shulman theorems are often schematic in cubes, topes, inclusions, and families that **do not live in RSTT contexts**. The system paper defines an **MPL** with five entry kinds (*verified*, Def. 3.3): cube parameters, tope parameters, tope inclusion assumptions, term parameters, type-family parameters.

**Implementation internalisation:** Rzk definitions take cubes / tope families / types as **first-class parameters**. Tope families `φ : {I | ψ} → TOPE` encode inclusions via domains; elaboration **inserts a domain conjunct** `φ(t) ↝ ψ(t) ∧ φ(t)` so inclusions reach the tope solver. Cleaner **tope subuniverses** tracking domains by typing are listed as future work (§9 / open questions in [10-open-questions.md](10-open-questions.md)).

---

## 5. Faithfulness and conservativity

Translation `τ` (MPL+RSTT → dRzk) is identity on cubes/topes/MLTT and re-encodes extension types as shape-Π of a restricted codomain (*verified*, Def. 5.1 / eq. (1)).

| Result | Statement | Status |
|--------|-----------|--------|
| **Faithfulness** | Every RSTT derivation maps to a dRzk derivation of the translated judgement | **Proved** (Prop. 5.4) |
| **Conservativity (ext-style)** | If dRzk inhabits `τ(T)` by a derivation with **ext-style hypotheses** (free-standing restrictions concluded but not assumed), RSTT inhabits `T` | **Proved** (Thm. 5.8) |
| **Full conservativity** | Same without the ext-style restriction | **Conjecture 5.9** (*open in literature*) |

*Verified practical note:* sHoTT’s ~450 restriction sites (paper’s count) sit on shape-Π codomains with boundary ⊨ shape, so the library stays in the proved fragment.

---

## 6. Algorithmic layer (implementation highlights)

From arXiv:2607.12207 §6 (*verified*):

- **Bidirectional** checking with ambient tope context; solver discharges shape inclusions.
- **Type-directed** restriction computation (cannot naïve-normalise before checking) — kin to cubical TT.
- Subtyping folded into definitional equality via a variance flag (coercion-free).
- Tope solver: sound prototype, **incomplete**, sufficient in practice for sHoTT.
- Equality may **case-split** on tope disjunctions (expensive; last resort).
- Soundness: accepted programs are dRzk-derivable if the solver is sound — carrying §5 guarantees to the checker.

**Soundness bugs found by formalising the rules** (*verified* intro): through v0.7.7, identity types compared without underlying types, and subtype polarity ran backwards in negative positions. Fixed in **v0.7.8** (PRs [#269](https://github.com/rzk-lang/rzk/pull/269), [#270](https://github.com/rzk-lang/rzk/pull/270)); sHoTT needed migration for the identity-type fix.

**Type-in-type:** Rzk (like some HoTT libraries) currently uses an unsound `U : U` convenience (*verified* in Yoneda paper’s Rzk overview and system paper tutorial footnotes); proper hierarchies remain future work.

---

## 7. Directed univalence / modalities

Beyond 2017 RSTT:

- Experimental Rzk modalities (`♭` / `♯` / `ᵒᵖ`) toward **Triangulated Type Theory**-style modes; docs `reference/modalities.rzk.md`.
- System paper cites **Talipov–Kudasov 2026** modal / directed-univalence work as ongoing (*verified* intro citation — retrieve that PDF before quoting details).
- Parallel non-RSTT model: Weaver–Licata bicubical directed univalence (LICS 2020) — different geometry; see [09-comparative-notes.md](09-comparative-notes.md).

Treat surface modality syntax as **unstable**.

---

## 8. What this means for “is Rzk exactly the 2017 paper?”

**Answer (*verified* synthesis):** Rzk is a **computational refinement** of RSTT: same three layers and extension-type idea; declarative split + subtyping make checking and intermediate types precise; MPL → first-class parameters; algorithm + solver make the paper’s silent tope side conditions machine-checkable. On the proved conservativity fragment, dRzk does not invent new theorems about translated RSTT types; **full** conservativity remains conjectural.
