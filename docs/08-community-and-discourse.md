# Community and discourse

Public venues, talks, blogs, and social-media signals around **Rzk**, **sHoTT**, and Riehl–Shulman synthetic ∞-category formalization. Dates use Asia/Singapore labels when converted from UTC; otherwise we keep the source’s stated date.

**Verification note.** Zulip, GitHub, arXiv, YouTube, and official MkDocs pages were reachable during research (2026-09-28). **Direct Twitter/X (and Nitter) search was not usable** from this environment (blocked / JS-walled search). X highlights below are therefore sparse and drawn from **secondary indexes** (nLab, conference pages, GitHub org) plus known public handles—not from a live scrape of threads. Treat X coverage as a **gap**.

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

1. Join **Zulip** for questions that are not yet issues.
2. Prefer **sHoTT PRs** for mathematics; **rzk** issues for checker/solver/LSP bugs.
3. Cite papers with arXiv + DOI when writing notes; link literate identifiers on `emilyriehl.github.io/yoneda` or `rzk-lang.github.io/sHoTT`.
4. Do not treat Zulip archives as citable publications unless a permalink is stable and the author agrees—summarize with permission when needed.
