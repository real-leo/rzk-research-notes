# Formalization case studies

Grounded case studies from **Kudasov–Riehl–Weinberger**, *Formalizing the ∞-categorical Yoneda lemma* ([arXiv:2309.08340](https://arxiv.org/abs/2309.08340), CPP 2024) and the Rzk **system paper** ([arXiv:2607.12207](https://arxiv.org/abs/2607.12207)). Literate artifacts: [emilyriehl/yoneda](https://github.com/emilyriehl/yoneda), living library [rzk-lang/sHoTT](https://github.com/rzk-lang/sHoTT).

---

## 1. Why formalize ∞-category theory in Rzk?

The Yoneda paper’s intro (*verified*): analytic ∞-category formalization forces an early **model choice** (quasicategories vs complete Segal spaces vs …) or a costly multi-model comparison library. Lean mathlib (at writing) had no ∞-category theory partly for this reason. Synthetic RSTT + a checker with **simplicial** extension types aims to prove theorems that interpret in complete Segal spaces / internal ∞-categories without picking coordinates in user proofs.

Cubical assistants supply **cubical** extension types; the paper argues that postulated Agda extensions + rewrite rules still miss rewriting for **application of a variable of extension type**, leaving bookkeeping. Rzk exists to make simplicial boundaries computational.

---

## 2. Case study: ∞-categorical Yoneda (absolute)

### Statement (synthetic)

For a **pre-∞-category** (Segal type) `A`, `a : A`, and **covariant** family `C : A → U`, the evaluation map

`evid : ((z : A) → hom A a z → C z) → C a`

sending `φ ↦ φ(a, id_a)` is an **equivalence** (`yoneda-lemma` in the literate library).

*Verified nuance:* the theorem is stated for **pre-∞-categories**, not only Rezk-complete ones.

### Proof outline (*paraphrased from §5*)

1. Inverse `yon` uses **covariant transport**: `u ↦ λ x λ f. f_* u`.
2. Naturality of fiberwise maps between covariant families is **automatic** (no separate naturality proof obligation of the 1-categorical style).
3. One composite uses identity transport; the other uses naturality + `f ∘ id = f` + function extensionality (twice).

### What formalization taught the paper authors (*verified*, §1.3)

The published RSTT proof of the “only if” direction of **Proposition 8.13** (covariance of representables ↔ Segal) used **circular reasoning**. Formalization made the cycle transparent (a lemma used the conclusion). The result remains true; the corrected proof (`is-segal-is-covariant-representable`) appears in arXiv:1705.07442**v5**.

Takeaway for these notes: synthetic proofs are short *because* naturality is often free, but the checker still catches real gaps in published mathematics.

---

## 3. Case study: dependent Yoneda

Dependent Yoneda (`dependent-yoneda-lemma`) is a **directed path-induction** principle: for covariant `C` over `Σ_(x:A) (hom A a x)`, evaluation at `(a, id_a)` is an equivalence. The absolute lemma follows. Semantically newer than classical ∞-cat literature at the time of RSTT; also appears later in Riehl–Verity ∞-cosmoi (§5).

System paper Example 3.5 / 5.3: stating dependent Yoneda cleanly needs **term parameters before type-family parameters** in the MPL — one reason Rzk exposes first-class parameters.

---

## 4. Comparison with 1-categorical Yoneda formalizations

From arXiv:2309.08340 §6 (*verified*):

| Setting | Library / assistant | Extra burden vs Rzk synthetic proof |
|---------|---------------------|-------------------------------------|
| Univalent 1-cats | **agda-unimath** (authors contributed a precategory Yoneda) | Naturality of `yon` is **explicit** data; representables as Set-valued functors |
| Set-based 1-cats | **Lean 3/4** (Hazratpour ports at authors’ request) | Tactic culture; Lean 4 `aesop_cat` can discharge some naturality after a lemma |
| Synthetic ∞ | **Rzk** yoneda repo | Naturality largely free; verbose without implicits/tactics |

Same *proof outline*; different encoding of “category” (structure vs property) and of representables (functors vs covariant families).

---

## 5. Scale: sHoTT as living case study

System paper §1.2 / §7.1 snapshot (*verified*):

- **>~25 000** lines, **~1 500** top-level declarations (paper’s numbers; re-measure on tip for updates — [10-open-questions.md](10-open-questions.md)).
- Topics: Segal/Rezk, covariant families, adjunctions, cocartesian fibrations, (co)limits.
- Lossin (2025) MSc: cocartesian fibrations contributed toward sHoTT (*cited* in system paper).
- Teaching: Regensburg ITP school 2023; ICERM Aug 2026 workshop sessions on Rzk.

Ongoing agenda (Yoneda paper §7 + sHoTT About; *not* invented here): finish adjunction equivalence zoo; complete (co)limit preservation; **cocartesian Yoneda**; directed univalence / modalities; better Rzk UX (implicits, incremental check, modules).

---

## 6. Cofibration composition as a “shape calculus” case

System paper §2.4 (*verified*): Riehl–Shulman Thm. 4.4 formalized as `cofibration-composition` — equivalence between extending `φ → χ` and factoring through intermediate `ψ`. Exercises:

- first-class cube/tope/family parameters,
- coercion-free subtyping on the inverse map,
- η-expanded forward map (Remark 4.5),
- solver-proved inclusions + restriction computation so `refl` closes round-trips.

Useful teaching example before Yoneda: pure **extension-type algebra**, no Segal hypothesis.

---

## 7. Formalization → checker soundness

Writing declarative/algorithmic rules for arXiv:2607.12207 exposed two released soundness bugs (through v0.7.7), fixed in v0.7.8 — see [11-metatheory-and-semantics.md](11-metatheory-and-semantics.md). Case-study moral: metatheory papers are not only “about” the math library; they audit the **implementation**.

---

## 8. Pointers into literate code

| Topic | Starting identifier / path |
|-------|----------------------------|
| Hom / Segal / Rezk | `hom`, `is-pre-∞-category` / `is-segal`, `is-∞-category` / `is-rezk` |
| Covariance | `is-covariant`, `dhom` |
| Yoneda | `yoneda-lemma`, `dependent-yoneda-lemma`, `evid`, `yon` |
| Extensionality | `funext`, `extext` / relative extension extensionality |
| Adjunctions (sHoTT) | `simplicial-hott/11-adjunctions.rzk` |
| Limits (sHoTT) | `simplicial-hott/13-limits.rzk` |

Rendered: https://emilyriehl.github.io/yoneda/ · https://rzk-lang.github.io/sHoTT/
