# Comparative notes: Rzk vs neighbours

Deeper comparison of **Rzk / RSTT / sHoTT** with **Cubical Agda**, other HoTT assistants, **directed type theory** proposals, and **graphical n-category** tools. Complements the landscape map in [07-related-work-landscape.md](07-related-work-landscape.md).

Tone: technical research notes. Short quotes only; paraphrase + cite.

---

## 1. Shared vocabulary, different statements

Many systems talk about **intervals**, **extension / path types**, and **synthetic homotopy**. The important split:

| Question | RSTT / Rzk answer | Cubical TT answer |
|----------|-------------------|-------------------|
| What is a 1-cell in a “space-like” type? | Directed map out of `2` / Δ¹ (hom-types via extension) | Path / map out of cubical `I` (invertible up to higher paths) |
| What is the headline theorem class? | Segal / Rezk, fibrations, ∞-Yoneda, (co)limits, adjunctions | Univalence, HITs, computational path algebra |
| Where do boundaries live? | Definitional restriction on **arbitrary topes** (simplicial shapes) | Face lattices / cofibrations of the **cube** |
| Are all types categories? | No—Segal/Rezk are *properties* of types | N/A—types are ∞-groupoids |

Riehl–Shulman’s design “accepts extra non-Segal types” so the HoTT toolkit remains available while carving out synthetic (∞,1)-categories ([01-type-theory-background.md](01-type-theory-background.md); [arXiv:1705.07442](https://arxiv.org/abs/1705.07442)).

---

## 2. Rzk vs Cubical Agda (and cubicaltt)

### 2.1 What Cubical Agda optimizes for

Cubical Agda (Vezzosi–Mörtberg–…; Agda ≥ 2.6 cubical mode) implements a computational reading of HoTT/UF: interval pretype, transport / `hcomp`, Glue, HITs with nested matching. Classic account: *Cubical Agda: A Dependently Typed Programming Language with Univalence and Higher Inductive Types* (JACM / staff.math.su.se PDF). Precursor: **cubicaltt** (Cohen–Coquand–Huber–Mörtberg).

### 2.2 What Rzk’s own docs claim

Upstream [Other proof assistants](https://rzk-lang.github.io/rzk/en/latest/related/) (*verified*): Cubical Agda “supports a variant of extension types found in Rzk, **albeit restricted to the use with cubical intervals**.” Notable libraries: `agda/cubical`, [1lab](https://1lab.dev).

### 2.3 What the Yoneda formalization paper claims

Kudasov–Riehl–Weinberger ([arXiv:2309.08340](https://arxiv.org/abs/2309.08340)) argue that cubical provers (Cubical Agda, red*, Aya, Arend) support **cubical** extension types, whereas the synthetic ∞-category development needs **simplicial** shape inclusions. They discuss (and set aside) postulating extensions in Agda with rewrite rules: rewriting for **application of a variable of extension type** is incomplete, forcing bookkeeping. Rzk was built to make those boundaries computational for simplicial topes.

### 2.4 Engineering culture

| Aspect | Rzk | Cubical Agda |
|--------|-----|--------------|
| Host language | Dedicated `rzk-1` + Haskell checker | Mode inside Agda |
| Tactics | Minimal (direct terms; tope automation) | Agda interactive editing; no Lean-style tactic language |
| Libraries | sHoTT / yoneda focused | Broad HoTT + cubical algebra |
| Style influence | Formatter borrows **agda-unimath** conventions | — |

*Inferred:* Cubical Agda will remain better for Brunerie-number / HIT-heavy homotopy; Rzk will remain better for Segal-space-style bookkeeping with judgmental endpoints.

### 2.5 Overlap worth exploiting pedagogically

Both teach “functions on an interval with fixed faces.” A student who knows Cubical Agda paths can learn Rzk homs as *directed analogues* with a second (categorical) direction in the intended bisimplicial semantics—without expecting Kan operations or Glue.

---


### 2.6 Metatheoretic status (system paper)

Cubical Agda’s metatheory is a decades-long cubical TT / canonicity literature. For Rzk, [arXiv:2607.12207](https://arxiv.org/abs/2607.12207) supplies the first published **faithfulness** proof of a translation RSTT → declarative Rzk and **conservativity on ext-style derivations**, with **full conservativity conjectural** (Conjecture 5.9). That is a different kind of “comparison to the paper semantics” than Cubical Agda’s relation to CCHM — closer to “does the assistant exceed the calculus we named?” Detail: [11-metatheory-and-semantics.md](11-metatheory-and-semantics.md).


## 3. Rzk vs redtt / cooltt / RedPRL

The **red\*** family (RedPRL Development Team; OCaml) explores **Cartesian cubical** type theory with interactive holes (Epigram/Agda/Idris lineage). Sterling’s note *redtt and the future of Cartesian cubical type theory* (<https://www.jonmsterling.com/sterling-2020-epa/>) describes cooltt’s push toward definitional η for cofibration disjunctions.

**Vs Rzk:**

- Same broad “experimental computational HoTT” vibe; different cube category and no RSTT tope layer.
- **Directed** experiments related to Weaver–Licata bicubical work sit closer to cooltt’s research circle than to Rzk’s simplicial shapes (*inferred* from citation graphs / thesis titles—not a claim that cooltt ships RSTT).
- ALGAE’s “libraries to assemble a checker” rhymes culturally with Rzk’s free-foil / E-unification “inference as a library” slogan—but stacks differ (OCaml vs Haskell SOAS).

---

## 4. Rzk vs classical HoTT assistants (Agda/Coq/Lean)

| | Rzk | Agda `--without-K` / Coq-HoTT / UniMath | Lean 4 mathlib |
|--|-----|----------------------------------------|----------------|
| ∞-groupoid HoTT | Partial (enough for sHoTT prelude); `hottbook` exploratory | Strong | Not native; Ground Zero experiments |
| ∞-category synthetic | **Primary niche** | Generally absent as RSTT | Absent |
| Proof style | Term-based; verbose without implicits | Mix; Agda interactive | Tactic-heavy |
| 1-cat Yoneda | Compared in CPP paper via agda-unimath + Lean ports | Mature | Mature (`CategoryTheory.Yoneda`) |

CPP 2024 contribution: same *proof outline* for Yoneda as 1-categorical formalizations, but naturality/functoriality often **comes for free** synthetically—highlighting the pedagogical thesis of Riehl’s Notices essay.

---

## 5. Rzk / sHoTT goals vs “analytic” ∞-category formalization

Analytic formalization (pick quasicategories *or* complete Segal spaces *or* … in a set-level library) faces model-choice and comparison overhead. RSTT + Rzk bet on:

1. Change the **foundation** so Segal/Rezk are short internal definitions.
2. Interpret into bisimplicial / simplicial objects in ∞-toposes (Shulman; Weinberger) so theorems transfer.

sHoTT’s public aim (About page): formalize results from Riehl–Shulman, Buchholtz–Weinberger, Bardomiano Martínez, following the undergraduate-accessibility philosophy of Riehl 2023 Notices.

**Limits of the bet** (honest): not all of Lurie HTT is in scope without directed HITs, universes for fibrations, modalities for opposite/core, etc. (future work sections of arXiv:2309.08340 and arXiv:2607.12207).

---

## 6. Directed type theory vs RSTT-in-Rzk

### 6.1 “Native” directed TT

Proposals (North; Licata–Harper; Nuyts; …) often make **hom-types primitive** and struggle historically with exponentiability, variance, and coherence. RSTT’s *indirect* route keeps Π/Σ/Id and adds shapes + extensions.

### 6.2 Bicubical directed univalence

Weaver–Licata (LICS 2020) give a **constructive model** of directed univalence in bicubical sets, with Agda formalization of the model—not the same as shipping an RSTT library of ∞-Yoneda. Parallel research line; geometry is cubical×cubical rather than simplicial shapes.

### 6.3 Modal / triangulated extensions in Rzk

Experimental modalities (`diruniv` / TTT) aim at directed univalence and opposites *inside* the Rzk ecosystem (docs `reference/modalities.rzk.md`; Talipov–Kudasov cited in system paper). Treat surface syntax as unstable ([05-limitations-and-roadmap.md](05-limitations-and-roadmap.md)).

---

## 7. Rzk vs homotopy.io and Catt

| | Rzk | homotopy.io | Catt |
|--|-----|-------------|------|
| User interaction | Textual literate Markdown / VS Code | Mouse string/surface diagrams | Textual pasting / `coh` |
| Object of study | Types with Segal/Rezk structure | Free associative n-cats on a signature | Pasting-scheme ω-cells |
| Homotopy | HoTT identity types + shapes | Homotopies as diagram deformations | Type equalities / reductions (`--su` etc.) |
| Best for | Theorem statements about ∞-cats | Calculating composites visually | Encoding coherences combinatorially |

FSCD 2024 homotopy.io paper emphasizes semistrict globular theory with weak interchangers; Catt (Finster; Benjamin–Mimram line) is the type-theoretic sibling in teaching materials (<https://www.cl.cam.ac.uk/~jv258/mgs2023/>).

*Inferred:* a research program might *bridge* (export string diagrams ↔ synthetic statements), but no such bridge is claimed by Rzk upstream today.

---

## 8. Implementation substrate vs mathematical competitors

Do not confuse **free-foil / SOAS / E-unification** with Cubical Agda:

- They explain Rzk’s binder representation and the roadmap toward dependent inference “as a library.”
- They do not decide simplicial vs cubical mathematics.
- Papers: FSCD 2023 E-unification; ICCQ 2024 Free Foil; foil IFL 2022.

---

## 9. Practical decision guide

| You want to… | Prefer |
|--------------|--------|
| Formalize synthetic ∞-categorical Yoneda / fibrations / (co)limits in RSTT style | **Rzk + sHoTT** |
| Compute with univalence / HITs / cubical library math | **Cubical Agda** |
| Large classical algebra + category theory in tactics | **Lean mathlib** (1-cats) |
| UF category theory without cubes | **agda-unimath** / UniMath |
| Draw n-dimensional composites | **homotopy.io** (or Catt for pasting syntax) |
| Explore directed univalence models | Weaver–Licata / modal Rzk literature (expect research-grade) |

---

## 10. Open comparison questions

See [10-open-questions.md](10-open-questions.md) and [11-metatheory-and-semantics.md](11-metatheory-and-semantics.md) for follow-ups (e.g. encoding RSTT in Cubical Agda with rewrites; **Conjecture 5.9** full conservativity; performance vs Agda on shared lemmas; directed univalence comparisons).
