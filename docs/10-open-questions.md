# Open questions (follow-up research)

Research prompts for later passes on Rzk / sHoTT / related work. Distinguishes **factual gaps** (we could not verify) from **mathematical / engineering open problems** (stated in papers or inferred as natural next steps).

---

## A. Gaps in *this* notes repository’s evidence

1. **Reddit corpus.** Arctic Shift API pass (2026-09-28) found no `title`/`body` hits for `rzk` in key subs; ID-verified adjacent threads — see [13](13-reddit-methodology-arctic-shift.md) and [08](08-community-and-discourse.md). Re-check after rate-limit cooloffs; still skip multi-TB dumps on small boxes.
2. **Twitter/X corpus.** Live search via Nitter / `site:x.com` failed in the research environment (2026-09-28). Recover dated posts/threads from Riehl, Kudasov/`fizruk`, and HoTT accounts; archive permalinks in [08-community-and-discourse.md](08-community-and-discourse.md).
3. **Zulip content.** We link the Zulip but did not scrape private/public streams. With permission, summarize recurring themes (solver pain points, implicits roadmap, teaching).
4. **Blog completeness.** Only two posts listed on the EN blog index at research time; check whether older announcements live only in GitHub Releases / Russian blog.
5. **Exact sHoTT metrics.** System paper cites ~25k LOC / ~1500 declarations—re-measure on current `main`/`develop` tips for these notes’ next snapshot.
6. **Soundness fix migration.** Document which sHoTT commits correspond to identity-type / subtyping polarity fixes (PRs #269/#270 lineage mentioned in arXiv:2607.12207) for historians of the library.

---

## B. Theory: RSTT ↔ Rzk

From Kudasov–Sim–Ahrens [arXiv:2607.12207](https://arxiv.org/abs/2607.12207):

1. **Full conservativity (Conjecture 5.9 in [arXiv:2607.12207](https://arxiv.org/abs/2607.12207)).** Conservativity of declarative Rzk over RSTT is **proved** for *ext-style hypotheses* (Thm. 5.8); full conservativity without that restriction is **conjectural**. Background: [11-metatheory-and-semantics.md](11-metatheory-and-semantics.md).
2. **Pointwise subsumption / η.** Typing not invariant under η-contraction of subjects in some extension-boundary cases; prototypes exist—should they land in the declarative theory?
3. **Tope subuniverses.** Inserted domain conjuncts for tope families are a practical elaboration trick; cleaner tope subuniverses tracking domains?
4. **Layer stratification.** Cubes/topes depending on types more liberally than paper RSTT—consistency impact?
5. **Type-in-type.** Standard experimental risk; universe hierarchy for Rzk?

---

## C. Formalization mathematics (sHoTT agenda)

Drawn from arXiv:2309.08340 §7, sHoTT About page, and system paper teaching citations:

1. Finish **adjunction equivalence zoo** (transposing vs diagrammatic, etc.).
2. Complete **limits/colimits** theorems (Bardomiano Martínez) and preservation results.
3. **Cocartesian Yoneda** and structural lemmas from Buchholtz–Weinberger.
4. **Directed univalence / modalities** on `diruniv`—stabilize syntax; compare to Weaver–Licata.
5. **∞-category of ∞-categories** and related recent arXiv lines (e.g. works citing simplicial TT in 2025–2026)—which fragments are Rzk-ready?
6. Encoding **analytic** model comparisons (CSS vs quasicategories) still out of scope—or bridge via two-level TT?

---

## D. Comparisons with other provers

1. **RSTT in Cubical Agda via rewrites / postulated extensions:** can the application-rewrite gap noted in arXiv:2309.08340 be closed with modern Agda features?
2. **Shared lemma benchmark:** port a small HoTT lemma suite to Rzk and Cubical Agda; compare LOC, definitional equality pain, compile time.
3. **homotopy.io ↔ Rzk:** is there a meaningful translation from associative n-cat diagrams to Segal-type statements (or vice versa)?
4. **Catt pasting vs simplicial shapes:** educational mapping for MGS-style courses.
5. **Lean Ground Zero / future Lean HoTT:** any path to RSTT-like shapes without forking Lean’s kernel?

---

## E. Implementation / UX

1. **Implicits and inference.** E-unification for SOAS ([arXiv:2302.05815](https://arxiv.org/abs/2302.05815))—what fraction of sHoTT annotations could disappear?
2. **free-foil cutover.** Dual AST debt ([02-architecture.md](02-architecture.md))—finish swap?
3. **Multi-file modules / incremental checking.** Blocker for large libraries and IDE snappiness.
4. **simple-topes merge.** User-defined cubes (cubical/globular variants) without hardcoding RSTT builtins.
5. **SVG / interactive shape rendering.** Extend beyond small demos for teaching (ICERM 2026 audience).
6. **Formatter stability** vs agda-unimath style drift.

---

## F. Community / teaching

1. What curriculum works for ICERM Aug 2026 / future schools (Regensburg 2023 lessons learned)?
2. Yoneda game completeness vs Lean Natural Number Game UX expectations.
3. Documentation languages (EN/RU)—priority for additional translations?
4. Citation hygiene for AI-assisted note repos (this one): keep paraphrase + URL discipline.

---

## G. Meta: how to extend these notes

When answering an item above:

1. Prefer primary sources (arXiv PDF, upstream Markdown, talk slides).
2. Mark **verified** vs **inferred**.
3. Update [sources.md](sources.md) with access date.
4. Avoid pasting long copyrighted passages—paraphrase, quote short phrases, cite URLs.

---

## H. Pointers into expanded notes

| Topic | Doc |
|-------|-----|
| Split extensions, MPL, solver, Conjecture 5.9 | [11-metatheory-and-semantics.md](11-metatheory-and-semantics.md) |
| Yoneda / sHoTT / cofibration narratives | [12-formalization-case-studies.md](12-formalization-case-studies.md) |
| Arctic Shift dump sizes + API results | [13-reddit-methodology-arctic-shift.md](13-reddit-methodology-arctic-shift.md) |
