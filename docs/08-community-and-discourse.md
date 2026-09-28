# Community and discourse

Public venues, talks, blogs, and social-media signals around **Rzk**, **sHoTT**, and Riehl–Shulman synthetic ∞-category formalization. Dates use Asia/Singapore labels when converted from UTC; otherwise we keep the source’s stated date.

**Verification note.** Zulip, GitHub, arXiv, YouTube, and official MkDocs pages were reachable during research (2026-09-28). **Direct Twitter/X (and Nitter) search was not usable** from this environment (blocked / JS-walled search). **Direct Reddit** (`reddit.com` / `old.reddit.com` HTML & JSON, PullPush) was also **network-blocked or rate-limited**; Reddit coverage below is reconstructed from **Google `site:reddit.com` indexes and public result snippets**, not from logged-in Reddit API dumps. Treat both X and deep Reddit comment trees as **partial / gap-prone**.

---

## Primary hangouts

| Venue | URL | What happens there |
|-------|-----|--------------------|
| **Rzk Zulip** | <https://rzk-lang.zulipchat.com/> · register <https://rzk-lang.zulipchat.com/register/> | Default community chat: formalization help, checker bugs, sHoTT PRs, tooling (*verified* in upstream `community.md` / README) |
| **GitHub org `rzk-lang`** | <https://github.com/rzk-lang> | Rzk, sHoTT, vscode-rzk, rzk-game, mkdocs plugins, etc. |
| **Upstream issues / PRs** | <https://github.com/rzk-lang/rzk/issues> | Language, solver, soundness, LSP, formatter |
| **Official blog** | <https://rzk-lang.github.io/rzk/en/blog/> | Announcements and tooling deep-dives |

---

## Blog posts (official)

*Verified* listing from <https://rzk-lang.github.io/rzk/en/blog/>:

| Date | Title | Notes |
|------|-------|-------|
| 2023-12-10 | *We have a blog now!* | Announces multilingual docs (EN/RU) + blog system; literate Rzk snippets in posts |
| 2023-12-24 | *Rzk Formatter* | Design write-up for `rzk format` (v0.7.0 / bugfix 0.7.3); ~8 min read |

Further changelog-level discourse lives in GitHub Releases / Stackage package notes (e.g. Hackage ChangeLog themes for SVG render, BNFC, free-foil bumps)—see [03-build-and-tooling.md](03-build-and-tooling.md) and [sources.md](sources.md).

---

## Talks and seminars (with links)

| When | Event | Speaker(s) | Artifact |
|------|-------|------------|----------|
| **2023-10-05** | HoTTEST (Homotopy Type Theory Electronic Seminar Talks) | Nikolai Kudasov (joint work with Riehl–Weinberger) | Slides: <https://www.math.uwo.ca/faculty/kapulkin/seminars/hottestfiles/Kudasov-2023-10-05-HoTTEST.pdf>; demo repo <https://github.com/fizruk/hottest-2023-rzk-demo>; nLab cites video for this talk |
| **2023-09** | ITP School Regensburg (*Interactions of Proof Assistants and Mathematics*) | Rzk / sHoTT teaching | Demo site <https://fizruk.github.io/itp-school-2023-demo/>; school hub <https://itp-school-2023.github.io> (*cited in arXiv:2607.12207*) |
| **2024-01** | CPP 2024 (POPL colocated, London) | Kudasov, Riehl, Weinberger | *Formalizing the ∞-categorical Yoneda lemma* — <https://popl24.sigplan.org/details/CPP-2024-papers/6/Formalizing-the-categorical-Yoneda-lemma>; companion pages <https://emilyriehl.github.io/yoneda/CPP-2024/> |
| **(undated upload)** | YouTube | Emily Riehl | *Formalizing ∞-category theory in the Rzk proof assistant* — <https://www.youtube.com/watch?v=-voVwvoa5QI> (*verified* title/URL via search; exact recording date not re-checked from description metadata) |
| **2026-08 (upcoming at research time)** | ICERM topical workshop | Teaching Higher Category Theory with Computers | <https://icerm.brown.edu/program/topical_workshop/tw-26-thc> — practical sessions on Rzk (*cited in arXiv:2607.12207*) |

---

## Key people and public profiles (non-exhaustive)

| Person | Role (public) | Starting points |
|--------|---------------|-----------------|
| **Nikolai Kudasov** (`fizruk`) | Rzk author / maintainer; free-foil / SOAS; Innopolis | <https://github.com/fizruk> · <https://fizruk.github.io/> · nLab [Nikolai Kudasov](https://ncatlab.org/nlab/show/Nikolai+Kudasov) |
| **Emily Riehl** | RSTT coauthor; yoneda / sHoTT collaborator; outreach | JHU page; Notices AMS essay; CPP coauthor; public X handle often cited as `@emilyriehl` (*handle not re-verified live*) |
| **Jonathan Weinberger** | Fibered synthetic ∞-cats; Yoneda coauthor; Chevalley follow-ups | Papers on arXiv (see [07](07-related-work-landscape.md)) |
| **Michael Shulman** | RSTT coauthor | Higher Structures paper; HoTT community |
| **Benedikt Ahrens** | Rzk system paper coauthor; early suggestion of an RSTT assistant (*acknowledged in arXiv:2309.08340*) | Delft affiliation on arXiv:2607.12207 |
| **Violetta Sim** | Rzk system paper coauthor | arXiv:2607.12207 |
| **sHoTT contributors** | Library authors (Bakke, Bardomiano Martínez, Lossin, Abounegm, …) | `sHoTT` `CONTRIBUTORS.md`; acknowledgements in CPP / system papers |

---

---

## Reddit discourse (sparse for Rzk itself)

**Bottom line.** As of the 2026-09-28 pass, we found **no Google-indexed Reddit thread whose primary subject is the Rzk proof assistant, `rzk-lang`, or the sHoTT library**. Searches for those strings mostly collide with unrelated usernames or return empty relevance. Public Rzk talk therefore still concentrates on **Zulip + GitHub**, not Reddit.

What *does* appear on Reddit is **adjacent** mathematical / HoTT discourse: Riehl–Shulman’s 2017 paper, Riehl talks on synthetic ∞-categories, computational HoTT (cubical vs simplicial mentioned in passing), directed HoTT proposals, and Cubical Agda. That background helps situate how little Reddit has absorbed the *assistant* even when it knows the *math*.

**Method limits (*honest*).** Live fetches of `old.reddit.com` / `.json` endpoints returned 403 “network policy” blocks; PullPush archive API rate-limited agent traffic. Thread titles, dates, score hints, and comment gists below come from **search-engine snippets**. Comment bodies were **not** re-read in full on Reddit itself—do not treat gists as complete transcripts.

### Subreddits checked (existence / relevance)

| Subreddit | Notes for this topic |
|-----------|----------------------|
| [r/dependent_types](https://www.reddit.com/r/dependent_types/) | Best early hit: link-post of Riehl–Shulman synthetic ∞-categories paper (2017) |
| [r/math](https://www.reddit.com/r/math/) | Riehl talks / ∞-category culture; not Rzk-specific |
| [r/types](https://www.reddit.com/r/types/) | Computational HoTT thread mentioning simplicial *and* cubical type theory |
| [r/homotopytypetheory](https://www.reddit.com/r/homotopytypetheory/) | **Exists**; cubical / CCHM / learning threads; no Rzk hit in our queries |
| [r/agda](https://www.reddit.com/r/agda/) | Cubical Agda paper share |
| [r/haskell](https://www.reddit.com/r/haskell/) | General HoTT curiosity; **no** verified Rzk / `rzk-lang` thread |
| [r/ProgrammingLanguages](https://www.reddit.com/r/ProgrammingLanguages/) | Occasional “directed HoTT / cubical TT as exotic research” mentions; Riehl named as HoTT motivator in at least one career thread |
| r/highercategorytheory | Resource lists (e.g. Riehl on simplicial sets); quiet niche |

### Threads closest to Rzk’s mathematical lineage

| Approx. date | Subreddit | Thread | Gist (paraphrased) | URL |
|--------------|-----------|--------|--------------------|-----|
| **2017-05-27** | r/dependent_types | *A Type Theory for Synthetic ∞-Categories* | Link-post (~9 pts, ~2 comments) to Riehl–Shulman material; comment points at [arXiv:1705.07442](https://arxiv.org/abs/1705.07442); OP notes continuity with earlier Toronto ideas. **Pre-dates Rzk.** | https://www.reddit.com/r/dependent_types/comments/6dnmpg/a_type_theory_for_synthetic_categories/ |
| **2018-09-16** | r/math | *The synthetic theory of ∞-categories vs the synthetic theory of ∞-categories…* | Share of Riehl slides (~28 pts); light meta jokes + pointer to video/book—not a formalization discussion. | https://www.reddit.com/r/math/comments/9g6rtz/the_synthetic_theory_of_categories_vs_the/ |
| **2018-01** (id `7pkwbh`) | r/types | *Homotopy type theory from computational perspective?* | Asks for computational accounts of univalence etc.; replies steer to **cubical** work and, in one comment, name **simplicial type theory** alongside cubical as parallel developments. Useful as rare Reddit co-mention of simplicial TT—not an Rzk review. | https://www.reddit.com/r/types/comments/7pkwbh/homotopy_type_theory_from_computational/ |
| **2016-01** (id `42j8vu`) | r/dependent_types | *Towards a Directed Homotopy Type Theory based on 4 Kinds of Variance* (Nuyts) | Directed HoTT research share—neighbour to RSTT’s directed goals, different design. | https://www.reddit.com/r/dependent_types/comments/42j8vu/towards_a_directed_homotopy_type_theory_based_on/ |
| **2019-12** (id `e9pgbw`) | r/agda | *Cubical Agda: A Dependently Typed Programming Language…* | Paper announcement for Cubical Agda—the usual Reddit “computational HoTT assistant” reference point (contrast with Rzk’s simplicial niche; see [09](09-comparative-notes.md)). | https://www.reddit.com/r/agda/comments/e9pgbw/cubical_agda_a_dependently_typed_programming/ |
| **2022-01** (id `s8wp2b`) | r/homotopytypetheory | *Anders CCHM/HTS Theorem Prover* | Cubical / CCHM tooling interest inside the HoTT subreddit—again cubical-centered. | https://www.reddit.com/r/homotopytypetheory/comments/s8wp2b/anders_cchmhts_theorem_prover/ |

### Broader Riehl / ∞-category Reddit (context only)

Examples indexed by Google but **not** about RSTT formalization in Rzk: r/math threads on ∞-categorical monadicity / Riehl–Verity, “question for higher category theorists,” book suggestions naming Riehl, r/mathbooks *Categorical Homotopy Theory*, r/highercategorytheory resource posts linking Riehl’s simplicial-sets note. These show Riehl’s name circulates; they do **not** evidence awareness of the Rzk checker.

### Scarcity interpretation (*inferred*)

1. Rzk’s user base is small and already coordinated on **Zulip**.
2. Reddit’s HoTT attention skews toward the **HoTT Book**, **Cubical Agda**, and career/learning questions—not experimental simplicial assistants.
3. The 2017 paper *was* link-posted once in r/dependent_types; six+ years later there is still no obvious “has anyone tried Rzk?” thread in the indexes we saw.

**Follow-up:** when Reddit is reachable, re-run `rzk`, `rzk-lang`, `sHoTT`, `Kudasov`, and “Yoneda”+Riehl+formalization searches inside r/haskell, r/dependent_types, r/homotopytypetheory, and r/ProgrammingLanguages; archive any new threads in the table above.


## Twitter / X highlights (limited)

**Status:** Live `site:x.com` / Nitter queries from the research box did **not** return usable post text (search pages blocked or empty). We therefore **cannot** honestly quote dated threads here.

**What we can say from secondary sources:**

- Emily Riehl maintains a public academic presence on X under a handle commonly given as **emilyriehl** in tertiary summaries; primary discourse for Rzk appears to live on **Zulip + GitHub**, not X (*inferred*).
- Conference/talk announcements (CPP 2024, HoTTEST 2023, Regensburg school, ICERM 2026) are the durable public record; prefer those URLs over unreproducible tweets.
- Project handles / tags to search manually when X is available: `rzk-lang`, `Rzk`, `sHoTT`, `fizruk`, Riehl, “simplicial HoTT”, “∞-categorical Yoneda”.

If a future pass recovers specific posts, add them as rows:

| Date (SGT) | Author | Link | One-line summary |
|------------|--------|------|------------------|
| — | — | — | *placeholder: none verified this pass* |

---

## Other discourse surfaces

- **nLab** — [Rzk](https://ncatlab.org/nlab/show/Rzk) (revised 2026-07-15 per page footer): short idea statement, links to arXiv:2607.12207, Yoneda paper, HoTTEST talk.
- **Hackage / Stackage** — package synopsis and version history amplify release news to the Haskell audience (<http://hackage.haskell.org/package/rzk>).
- **HoTT community seminars** — HoTTEST archive under Kapulkin’s Western page is the indexed seminar trail for Kudasov’s talk.
- **Teaching / games** — Warm-up and Yoneda games (<https://rzk-lang.github.io/warmup-game/>, <https://rzk-lang.github.io/yoneda-game/>) are public onboarding discourse parallel to Lean games.

---

## How to engage (practical)

1. Join **Zulip** for questions that are not yet issues (Reddit is **not** currently a primary Rzk support channel).
2. Prefer **sHoTT PRs** for mathematics; **rzk** issues for checker/solver/LSP bugs.
3. Cite papers with arXiv + DOI when writing notes; link literate identifiers on `emilyriehl.github.io/yoneda` or `rzk-lang.github.io/sHoTT`.
4. Do not treat Zulip archives as citable publications unless a permalink is stable and the author agrees—summarize with permission when needed.
5. If posting on Reddit about Rzk, prefer precise links (playground, sHoTT docs, arXiv) so the sparse public trail stays high-signal.
