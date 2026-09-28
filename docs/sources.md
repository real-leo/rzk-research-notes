# Sources and bibliography

Dates are publication or release dates where known. Links accessed during research on **2026-09-28** (Asia/Singapore, UTC+8), unless noted.

**Method note.** We paraphrase and cite; we do **not** paste long verbatim copyrighted passages. Short phrases in quotes are for terminology anchors only. Twitter/X could **not** be searched live (blocked). Reddit HTML/JSON was often network-blocked; a later pass used the **arctic_shift API** ([13-reddit-methodology-arctic-shift.md](13-reddit-methodology-arctic-shift.md)). Some Reddit URLs below remain from Google `site:reddit.com` indexes—see [08-community-and-discourse.md](08-community-and-discourse.md).

---

## Foundational papers (RSTT / sHoTT math)

1. Emily Riehl & Michael Shulman. *A type theory for synthetic ∞-categories*. Higher Structures 1(1), 147–224, **2017**.  
   https://arxiv.org/abs/1705.07442  
   (Corrected post-publication v5 acknowledges typos / fixes noted by Cnossen, Kudasov, Licata, Sattler; circularity fix related to formalization.)

2. Ulrik Buchholtz & Jonathan Weinberger. *Synthetic fibered (∞,1)-category theory*. Higher Structures 7 (2023), 74–165.  
   https://arxiv.org/abs/2105.01724 · https://doi.org/10.21136/HS.2023.04

3. César Bardomiano Martínez. *Limits and colimits of synthetic ∞-categories*.  
   https://arxiv.org/abs/2202.12386 · MSCS vol. 35 (2025) e24 (publisher PDF via Cambridge)

4. Jonathan Weinberger. *Generalized Chevalley criteria in simplicial homotopy type theory*. **2024**.  
   https://arxiv.org/abs/2403.08190

5. Emily Riehl. *Could ∞-category theory be taught to undergraduates?* Notices of the AMS, May **2023**.  
   https://www.ams.org/journals/notices/202305/noti2692/noti2692.html

---

## Rzk formalization and system papers

6. Nikolai Kudasov, Emily Riehl, Jonathan Weinberger. *Formalizing the ∞-categorical Yoneda lemma*. CPP 2024 / POPL 2024 workshops.  
   https://arxiv.org/abs/2309.08340 · https://doi.org/10.1145/3636501.3636945  
   Conference page: https://popl24.sigplan.org/details/CPP-2024-papers/6/Formalizing-the-categorical-Yoneda-lemma  
   Companion: https://emilyriehl.github.io/yoneda/ · https://emilyriehl.github.io/yoneda/CPP-2024/  
   (First machine-checked ∞-Yoneda; circularity fix → arXiv:1705.07442v5; 1-cat comparisons in agda-unimath / Lean.)
   Notes digest: [12-formalization-case-studies.md](12-formalization-case-studies.md).

7. Nikolai Kudasov, Violetta Sim, Benedikt Ahrens. *Rzk: a Proof Assistant for Synthetic ∞-Categories*.  
   https://arxiv.org/abs/2607.12207  
   (Declarative vs algorithmic Rzk; faithfulness; conservativity Thm. 5.8 / Conjecture 5.9; split extension types; tope solver; sHoTT ~25k LOC snapshot.)
   Notes digest: [11-metatheory-and-semantics.md](11-metatheory-and-semantics.md), [12-formalization-case-studies.md](12-formalization-case-studies.md).

---

## Implementation / SOAS / tope solver

8. Nikolai Kudasov. *Functional Pearl: Dependent type inference via free higher-order unification*. **2022**.  
   https://arxiv.org/abs/2204.05653

9. Nikolai Kudasov. *E-Unification for Second-Order Abstract Syntax*. FSCD 2023, LIPIcs 260.  
   https://doi.org/10.4230/LIPIcs.FSCD.2023.10 · https://arxiv.org/abs/2302.05815

10. Nikolai Kudasov. *Experimental prover for Tope logic*. SCAN 2023, pp. 37–39.  
    https://www.mathnet.ru/ConfLogos/2220/abstracts.pdf#page=38

11. Dougal Maclaurin, Alexey Radul, Adam Paszke. *The Foil: Capture-Avoiding Substitution With No Sharp Edges*. IFL 2022.  
    ACM DL entry via foil citations in free-foil README.

12. Nikolai Kudasov, Renata Shakirova, Egor Shalagin, Karina Tyulebaeva. *Free Foil: Generating Efficient and Scope-Safe Abstract Syntax*. ICCQ 2024.  
    https://doi.org/10.1109/ICCQ60895.2024.10576867 · https://github.com/fizruk/free-foil · arXiv companion commonly linked from README

---

## Cubical / Cartesian cubical / related assistants

13. Cyril Cohen, Thierry Coquand, Simon Huber, Anders Mörtberg. *Cubical Type Theory: A Constructive Interpretation of the Univalence Axiom*. TYPES 2015 / LIPIcs.  
    https://doi.org/10.4230/LIPIcs.TYPES.2015.5

14. Andrea Vezzosi, Anders Mörtberg, et al. Cubical Agda papers / docs.  
    https://agda.readthedocs.io/en/latest/language/cubical.html  
    PDF commonly cited: https://staff.math.su.se/anders.mortberg/papers/cubicalagda2.pdf

15. Jonathan Sterling. *redtt and the future of Cartesian cubical type theory* (EPA note).  
    https://www.jonmsterling.com/sterling-2020-epa/

16. Angiuli–Brunerie–Coquand–Favonia–Harper–Licata et al. Cartesian cubical type theory (syntax/models).  
    e.g. https://research.chalmers.se/publication/547296/file/547296_Fulltext.pdf

---

## Directed type theory (non-RSTT pointers)

17. Paige Randall North. *Towards a directed homotopy type theory*. MFPS / [arXiv:1807.10566](https://arxiv.org/abs/1807.10566).

18. Matthew Z. Weaver & Daniel R. Licata. *A Constructive Model of Directed Univalence in Bicubical Sets*. LICS 2020.  
    https://dl.acm.org/doi/10.1145/3373718.3394794 · author PDF https://dlicata.wescreates.wesleyan.edu/pubs/wl20bicubical/wl20bicubical.pdf

---

## Graphical / pasting higher categories

19. Lukas Heidemann, Nick Hu, Jamie Vicary, et al. *homotopy.io: A Proof Assistant for Finitely-Presented Globular n-Categories*. FSCD 2024.  
    https://drops.dagstuhl.de/storage/00lipics/lipics-vol299-fscd2024/LIPIcs.FSCD.2024.30/LIPIcs.FSCD.2024.30.pdf  
    Tool: https://homotopy.io · nLab: https://ncatlab.org/nlab/show/homotopy.io

20. Eric Finster et al. Catt / catt.io — pasting-scheme proof assistants.  
    https://github.com/ericfinster/catt · teaching notes https://www.cl.cam.ac.uk/~jv258/mgs2023/

---

## Talks, teaching, encyclopedic pages

21. Nikolai Kudasov. *Rzk proof assistant and simplicial HoTT formalization*. HoTTEST, **2023-10-05**.  
    Slides: https://www.math.uwo.ca/faculty/kapulkin/seminars/hottestfiles/Kudasov-2023-10-05-HoTTEST.pdf  
    Demo: https://github.com/fizruk/hottest-2023-rzk-demo

22. Emily Riehl. *Formalizing ∞-category theory in the Rzk proof assistant* (video).  
    https://www.youtube.com/watch?v=-voVwvoa5QI

23. ITP School Regensburg 2023 — Rzk demos.  
    https://itp-school-2023.github.io · https://fizruk.github.io/itp-school-2023-demo/

24. ICERM workshop *Teaching Higher Category Theory with Computers* (Aug **2026**).  
    https://icerm.brown.edu/program/topical_workshop/tw-26-thc

25. nLab: *Rzk*. https://ncatlab.org/nlab/show/Rzk (page footer revision **2026-07-15**)

---

## Upstream software (survey snapshot)

| Artifact | Location | Notes |
|----------|----------|-------|
| Rzk source | https://github.com/rzk-lang/rzk | Default branch `develop`; BSD-3 |
| Release v0.11.3 | https://github.com/rzk-lang/rzk/releases/tag/v0.11.3 | **2026-08-31** |
| MkDocs English docs | https://rzk-lang.github.io/rzk/ | Built from `docs/docs/en/` |
| Related assistants page | https://rzk-lang.github.io/rzk/en/latest/related/ | Agda, Cubical Agda, red*, Coq, Lean, … |
| Community page | https://rzk-lang.github.io/rzk/en/latest/community/ | Zulip CTA |
| Official blog | https://rzk-lang.github.io/rzk/en/blog/ | Formatter post 2023-12-24; blog launch 2023-12-10 |
| Hackage | http://hackage.haskell.org/package/rzk | |
| sHoTT | https://github.com/rzk-lang/sHoTT · https://rzk-lang.github.io/sHoTT/ | |
| yoneda | https://github.com/emilyriehl/yoneda | |
| vscode-rzk | https://github.com/rzk-lang/vscode-rzk | |
| rzk-game | https://github.com/rzk-lang/rzk-game | |
| simple-topes | https://github.com/fizruk/simple-topes | |
| Zulip | https://rzk-lang.zulipchat.com | |
| Org landing | https://github.com/rzk-lang | |

---

## Modal / TTT background (as cited by Rzk docs)

- Gratzer, Weinberger, Buchholtz — Triangulated Type Theory / multimodal lines (see Rzk `reference/modalities.rzk.md` footnotes for upstream’s precise pointers).
- Talipov & Kudasov — directed univalence / modal Rzk work cited in arXiv:2607.12207 (retrieve exact bibliographic key from that PDF when quoting).

---

---

## Reddit (Google-indexed; sparse for Rzk)

Accessed indirectly via Google `site:reddit.com` on **2026-09-28** (Asia/Singapore). Direct Reddit fetches from the research box were blocked.

### No primary Rzk threads verified

Queries for `Rzk`, `rzk-lang`, `sHoTT`, and close variants did **not** surface a thread primarily about the assistant. Do not invent Reddit buzz that is not there.

### Adjacent threads (mathematical / HoTT neighbours)

- https://www.reddit.com/r/dependent_types/comments/6dnmpg/a_type_theory_for_synthetic_categories/ — Riehl–Shulman synthetic ∞-categories link-post (**2017-05-27**)
- https://www.reddit.com/r/math/comments/9g6rtz/the_synthetic_theory_of_categories_vs_the/ — Riehl synthetic ∞-categories talk slides (**2018-09-16**)
- https://www.reddit.com/r/types/comments/7pkwbh/homotopy_type_theory_from_computational/ — computational HoTT; comment mentions simplicial + cubical TT
- https://www.reddit.com/r/dependent_types/comments/42j8vu/towards_a_directed_homotopy_type_theory_based_on/ — Nuyts directed HoTT
- https://www.reddit.com/r/agda/comments/e9pgbw/cubical_agda_a_dependently_typed_programming/ — Cubical Agda paper
- https://www.reddit.com/r/homotopytypetheory/comments/s8wp2b/anders_cchmhts_theorem_prover/ — CCHM/HTS prover discussion
- https://www.reddit.com/r/homotopytypetheory/ — subreddit hub (exists; mostly non-Rzk HoTT)




## Arctic Shift / Reddit archive tooling

- Arthur Heitmann. *Project Arctic Shift* — https://github.com/ArthurHeitmann/arctic_shift  
  README, `api/README.md`, `download_links.md`, `file_content_explanations.md` (cloned 2026-09-28).  
  API base: https://arctic-shift.photon-reddit.com · Search UI · Download tool.  
  Evaluation: [13-reddit-methodology-arctic-shift.md](13-reddit-methodology-arctic-shift.md).
- Academic Torrents aggregate dump ~3.12 TB (2005-06–2024-12), infohash `ba051999301b109eab37d16f027b3f49ade2de13` (size from torrent listing page).

## Unreachable / incomplete this pass

| Source class | Status |
|--------------|--------|
| Twitter/X posts & threads | **Not retrieved** (search/Nitter blocked); no permalinks verified |
| Reddit live HTML / JSON / PullPush | Often **blocked or rate-limited**; Google snippets + **arctic_shift API** |
| Dedicated Reddit threads about Rzk / rzk-lang / sHoTT | **None verified** (Google + arctic_shift scoped `rzk` queries; scarcity is a finding) |
| arctic_shift full dump ingest | **Not attempted** (multi-TB; see [13](13-reddit-methodology-arctic-shift.md)) |
| Full Zulip archives | Not scraped (privacy / login) |
| Some publisher PDFs behind paywalls | Used arXiv HTML/PDF where possible |
| Every paper citing 1705.07442 since 2024 | Sampled only (Weinberger Chevalley; fibered; limits; system paper) |
