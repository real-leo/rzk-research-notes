# Related-work landscape

Map of proof assistants, formalization projects, and mathematical frameworks that sit near **Rzk** / **simplicial HoTT (sHoTT)** / **Riehl–Shulman type theory with shapes (RSTT)**. This note synthesizes public docs and papers; it is **not** an exhaustive survey of all directed type theory.

**Verified vs inferred.** Items marked *verified* were checked against a primary URL or arXiv abstract during research (2026-09-28, Asia/Singapore). Items marked *inferred* summarize secondary accounts or our reading of how niches relate; treat those as hypotheses for follow-up.

---

## Positioning Rzk in one paragraph

Rzk implements a **computational refinement** of Riehl–Shulman simplicial type theory for **synthetic (∞,1)-categories** (Segal / Rezk types, extension types over directed shapes, automated tope solving). Ordinary HoTT assistants (Agda `--without-K`, Cubical Agda, Coq-HoTT, UniMath) target **∞-groupoids**. Graphical / pasting-scheme tools (homotopy.io, Catt) target **strict or semistrict n-categories** with different syntax. Cubical assistants share *extension-like* boundary computation with Rzk but over **undirected** intervals. Directed type theories (North, Weaver–Licata bicubical, experimental cooltt forks, Rzk modalities) aim at non-invertible 1-cells with varying geometry and maturity.

Primary Rzk refs: upstream docs <https://rzk-lang.github.io/rzk/>; system paper Kudasov–Sim–Ahrens, *Rzk: a Proof Assistant for Synthetic ∞-Categories*, [arXiv:2607.12207](https://arxiv.org/abs/2607.12207); nLab [Rzk](https://ncatlab.org/nlab/show/Rzk).

---

## Comparison table (high level)

| System / project | Geometry / paths | Directed 1-cells? | Maturity / niche | Relation to Rzk |
|------------------|------------------|-------------------|------------------|-----------------|
| **Rzk** + sHoTT | Simplicial shapes + topes; directed interval `2`; also Dedekind `𝕀` | Yes (synthetic ∞-cats via Segal/Rezk) | Experimental; substantial sHoTT library | — |
| **Cubical Agda** / cubicaltt | Cubical interval; Kan ops; Glue | No (groupoidal) | Production-grade HoTT | Shares extension-style boundaries; different goals (*verified*: Rzk `related.md`) |
| **redtt / cooltt / RedPRL** | Cartesian cubical | No (core); directed experiments exist elsewhere | Research cubical | Listed in Rzk “other assistants”; OCaml / RedPRL ecosystem |
| **Arend** / **Aya** | Interval / cubical-ish | No | JetBrains / experimental Java | Catalogued by Rzk docs |
| **Agda `--without-K`**, **HoTT-Agda**, **agda-unimath** | Path / axiomatic univalence | No | Large libraries | Syntax/style influence on Rzk formatter; 1-cat Yoneda comparison in CPP paper |
| **Coq-HoTT**, **UniMath** | Axiomatic HoTT / UF | No | Long-running | Classical HoTT formalization path |
| **Lean Ground Zero** / Lean 2 HoTT | CIC + HoTT scope hacks | No | Niche / historical | Rzk docs note Lean 3/4 dropped native HoTT mode |
| **homotopy.io** | Globular associative n-cats; string/surface diagrams | Higher cells; not RSTT synthesis | Interactive web tool | Complementary UI for n-cats; not a type theory with shapes |
| **Catt / catt.io** | Pasting schemes / ω-cats | Strict(ish) higher cats | Research | Type-theoretic pasting; different from simplicial HoTT |
| **Weaver–Licata bicubical** | Bicubes + directed univalence model | Yes (directed) | Model + Agda formalization of model | Parallel *synthetic directed* line; different cube geometry |
| **North directed HoTT** | Hom-types / Cat semantics | Yes | Foundational proposals | Conceptual neighbour; not Rzk’s implementation path |
| **free-foil / SOAS / E-unification** | Meta-theory of binders | N/A | Libraries + papers (Kudasov et al.) | Implementation substrate of Rzk, not a competitor assistant |

---

## Mathematical line: RSTT and follow-ups

*Verified primary papers:*

1. **Riehl–Shulman 2017** — *A type theory for synthetic ∞-categories*, Higher Structures 1(1), [arXiv:1705.07442](https://arxiv.org/abs/1705.07442). Introduces shapes, extension types, Segal/Rezk, covariant fibrations, directed Yoneda.
2. **Buchholtz–Weinberger 2023** — *Synthetic fibered (∞,1)-category theory*, Higher Structures 7, [arXiv:2105.01724](https://arxiv.org/abs/2105.01724). Cocartesian fibrations, Chevalley criteria, etc., in simplicial HoTT; actively formalized toward sHoTT.
3. **Bardomiano Martínez** — *Limits and colimits of synthetic ∞-categories*, [arXiv:2202.12386](https://arxiv.org/abs/2202.12386) (also MSCS 2025). Feeding sHoTT `13-limits` work.
4. **Weinberger** — *Generalized Chevalley criteria in simplicial homotopy type theory*, [arXiv:2403.08190](https://arxiv.org/abs/2403.08190).
5. **Kudasov–Riehl–Weinberger 2024 (CPP)** — *Formalizing the ∞-categorical Yoneda lemma*, [arXiv:2309.08340](https://arxiv.org/abs/2309.08340), DOI [10.1145/3636501.3636945](https://doi.org/10.1145/3636501.3636945). First machine-checked ∞-cat Yoneda in Rzk; compares to agda-unimath / Lean 1-cat Yoneda.
6. **Kudasov–Sim–Ahrens** — Rzk system paper [arXiv:2607.12207](https://arxiv.org/abs/2607.12207): declarative vs algorithmic Rzk, faithfulness/conservativity vs RSTT, split extension types, coercion-free subtyping, tope solver; reports sHoTT scale (~25k LOC / ~1500 decls in the paper’s snapshot) and soundness fixes (v0.7.8 lineage).

*Pedagogical / outreach:*

- Riehl, *Could ∞-category theory be taught to undergraduates?*, Notices AMS May 2023 — <https://www.ams.org/journals/notices/202305/noti2692/noti2692.html>. Explicitly cited as philosophy for sHoTT.
- ICERM workshop *Teaching Higher Category Theory with Computers* (Aug 2026) builds practical sessions on Rzk (*verified* via arXiv:2607.12207 abstract/intro citation of <https://icerm.brown.edu/program/topical_workshop/tw-26-thc>).

---

## Formalization projects tied to Rzk

| Project | URL | Role |
|---------|-----|------|
| **sHoTT** | <https://github.com/rzk-lang/sHoTT> · docs <https://rzk-lang.github.io/sHoTT/> | Living library: Segal/Rezk, fibrations, adjunctions, (co)limits, modal/diruniv branch |
| **yoneda** | <https://github.com/emilyriehl/yoneda> · <https://emilyriehl.github.io/yoneda/> | Frozen comparative Yoneda formalization (paper companion) |
| **hottbook** | <https://rzk-lang.github.io/hottbook/> | Exploratory HoTT Book port in Rzk |
| **simple-topes** | <https://github.com/fizruk/simple-topes> | Standalone tope/cube axiomatization experiment; merge path into Rzk |
| **rzk-game / yoneda-game** | <https://rzk-lang.github.io/yoneda-game/> | Lean-games-style teaching front-end |

---

## Cubical and Cartesian cubical family

- **Cubical Agda** (Vezzosi et al.) embeds CCHM-style cubical TT in Agda: computational univalence, HITs, path types as maps from an interval. Rzk’s official comparison notes that Cubical Agda supports a **variant of extension types restricted to cubical intervals**, whereas Rzk’s extensions are over **arbitrary (esp. simplicial) topes** ([related page](https://rzk-lang.github.io/rzk/en/latest/related/)).
- **cubicaltt** — prototype precursor; Haskell.
- **redtt / cooltt / RedPRL** — Cartesian cubical interactive assistants (RedPRL Development Team); cooltt emphasizes cofibration disjunction η. Related **ALGAE** libraries aim at composable checker cores (<https://redprl.org>).
- **Arend**, **Aya** — Java-based HoTT/cubical-ish systems listed upstream.

*Inferred:* none of these are drop-in replacements for RSTT formalizations; porting ∞-categorical Yoneda as in arXiv:2309.08340 would require encoding shapes differently (e.g. postulated extensions + rewrite rules—an approach the CPP paper discusses and rejects as incomplete for variable applications).

---

## Graphical and pasting-scheme higher-category tools

- **homotopy.io** — web proof assistant for finitely presented **associative n-categories** (Dorn–Douglas–Vicary line); mouse-driven string/surface diagrams (FSCD 2024 paper; nLab [homotopy.io](https://ncatlab.org/nlab/show/homotopy.io); <https://homotopy.io>). Globular, semistrict; visualization-first.
- **Catt / catt.io** (Finster et al.) — type theory with **pasting schemes** for ω-categorical composition; textual `coh` declarations. Cambridge MGS notes compare Catt vs homotopy.io: <https://www.cl.cam.ac.uk/~jv258/mgs2023/>.

*Inferred contrast with Rzk:* these tools prove statements *inside* a chosen higher-categorical syntax; Rzk proves statements *about* synthetic ∞-categories living as ordinary types in a HoTT-like universe. Overlap is cultural (higher cats + computers), not interchangeable kernels.

---

## Directed type theory (non-RSTT)

Selected public lines (paraphrased; see sources.md for URLs):

- **Licata–Harper**, **Nuyts**, **North** (*Towards a directed homotopy type theory*, [arXiv:1807.10566](https://arxiv.org/abs/1807.10566)) — foundational designs with directed hom-types / variance.
- **Weaver–Licata** — *A Constructive Model of Directed Univalence in Bicubical Sets* (LICS 2020); Agda-formalized model; later directed cooltt / thesis work (*inferred* from paper abstracts and Princeton DataSpace handle for bicubical DTT).
- **Rzk modalities / Triangulated Type Theory** — experimental `♭`/`♯`/`ᵒᵖ` and sHoTT `diruniv` toward directed univalence (Talipov–Kudasov cited in arXiv:2607.12207).
- **Two-level type theory / opetopic / globular type theories** — alternate routes to higher cats (see CPP related-work section of arXiv:2309.08340).

Honest gap: this landscape changes quickly; we did **not** exhaustively verify every directed cooltt commit or every Agda formalization claiming “simplicial type theory” fragments in Cubical Agda.

---

## Implementation literature (SOAS / free-foil)

Rzk is also a **Haskell implementation research vehicle**:

- Maclaurin–Radul–Paszke, *The Foil* (IFL 2022) — efficient capture-avoiding substitution.
- Kudasov et al., *Free Foil* (ICCQ 2024) — <https://github.com/fizruk/free-foil>; [IEEE / arXiv companion](https://doi.org/10.1109/ICCQ60895.2024.10576867).
- Kudasov, *E-Unification for Second-Order Abstract Syntax* (FSCD 2023), [arXiv:2302.05815](https://arxiv.org/abs/2302.05815).
- Kudasov, *Dependent type inference via free higher-order unification*, [arXiv:2204.05653](https://arxiv.org/abs/2204.05653).
- Downstream experiments: e.g. `evermake/free-foil-typecheck` toward generic bidirectional / HM checkers on free-foil.

These are **orthogonal** to the mathematical comparison with Cubical Agda: they explain why Rzk’s binder story and future inference plan look the way they do (see [02-architecture.md](02-architecture.md)).

---

## Takeaway for readers of these notes

If the goal is **synthetic ∞-category theorems in the Riehl–Shulman style**, Rzk + sHoTT is currently the dedicated executable path. If the goal is **computational univalence / HITs / classical HoTT libraries**, use Cubical Agda (or Coq-HoTT / UniMath). If the goal is **diagrammatic n-category calculation**, try homotopy.io or Catt. If the goal is **foundational directed TT design**, read North / Weaver–Licata / modal Rzk papers—and expect less library maturity than sHoTT’s Segal–Yoneda core.

---

## Citation-grounded feature matrix

Finer table than the high-level map above. Cells are *verified* against the cited source unless marked *inferred*.

| Feature | Rzk / RSTT | Cubical Agda | Weaver–Licata bicubical | homotopy.io / Catt |
|---------|------------|--------------|-------------------------|--------------------|
| Directed 1-cells as data | Yes — homs via extension out of `2` / `Δ¹` ([arXiv:1705.07442](https://arxiv.org/abs/1705.07442)) | No — paths invertible up to higher paths | Yes — directed univalence model (LICS 2020) | Higher cells in globular/pasting syntax |
| Extension / boundary computation | Arbitrary (esp. simplicial) topes ([related](https://rzk-lang.github.io/rzk/en/latest/related/); [arXiv:2309.08340](https://arxiv.org/abs/2309.08340)) | Cubical interval / Kan ops | Bicubes | N/A (diagram isotopy / `coh`) |
| Segal / Rezk as *properties* of types | Yes | N/A | Different directed stack | N/A |
| Machine-checked ∞-Yoneda | Yes — [arXiv:2309.08340](https://arxiv.org/abs/2309.08340) | Not in RSTT form | Not claimed | Not a HoTT library |
| Conservativity vs paper RSTT | Faithful + ext-style conservative; full conj. ([arXiv:2607.12207](https://arxiv.org/abs/2607.12207) Thm. 5.8 / Conj. 5.9) | — | — | — |
| Primary UX | Literate `rzk-1` + VS Code / games | Agda interactive | Agda model code | Mouse diagrams / pasting text |

Metatheory deep dive: [11-metatheory-and-semantics.md](11-metatheory-and-semantics.md). Formalization narratives: [12-formalization-case-studies.md](12-formalization-case-studies.md).
