# Rzk research notes

Deep research notes on **[Rzk](https://github.com/rzk-lang/rzk)**, an experimental Haskell proof assistant for **synthetic ∞-categories**, based on Riehl–Shulman’s *A type theory for synthetic ∞-categories* ([arXiv:1705.07442](https://arxiv.org/abs/1705.07442)).

This repository is **not** upstream documentation. It is an independent survey that synthesizes the Rzk codebase (`rzk-lang/rzk`, default branch `develop`), official MkDocs English docs, related formalization projects, papers, talks, and web discourse—so a reader can understand design choices, architecture, maturity, and **how Rzk sits among neighbouring systems**—without starting from zero.

**Upstream:** [https://github.com/rzk-lang/rzk](https://github.com/rzk-lang/rzk)  
**Official site / docs:** [https://rzk-lang.github.io/rzk/](https://rzk-lang.github.io/rzk/)  
**Surveyed version:** `rzk` **v0.11.3** (released 2026-08-31; `CITATION.cff` / Hackage), clone tip on `develop` at research time.  
**System paper:** Kudasov–Sim–Ahrens, [arXiv:2607.12207](https://arxiv.org/abs/2607.12207).

## How to navigate

| Doc | Contents |
|-----|----------|
| [docs/00-overview.md](docs/00-overview.md) | What Rzk is, problem domain, maturity |
| [docs/01-type-theory-background.md](docs/01-type-theory-background.md) | Shapes / cubes / topes / extension types (Riehl–Shulman) + post-2017 math pointers |
| [docs/02-architecture.md](docs/02-architecture.md) | Monorepo layout, CLI, typechecker, free-foil, parser, LSP, WASM |
| [docs/03-build-and-tooling.md](docs/03-build-and-tooling.md) | Stack / Cabal / Nix, install, `rzk.yaml`, tests, CI |
| [docs/04-ecosystem.md](docs/04-ecosystem.md) | sHoTT, yoneda, VS Code, games, Zulip, Hackage |
| [docs/05-limitations-and-roadmap.md](docs/05-limitations-and-roadmap.md) | Experimental status, multi-file deps, E-unification, simple-topes |
| [docs/06-getting-started-notes.md](docs/06-getting-started-notes.md) | Practical first steps for newcomers |
| [docs/07-related-work-landscape.md](docs/07-related-work-landscape.md) | Map of related proof assistants / formalizations vs Rzk |
| [docs/08-community-and-discourse.md](docs/08-community-and-discourse.md) | Zulip, blogs, talks; Reddit (sparse) + Twitter/X gaps |
| [docs/09-comparative-notes.md](docs/09-comparative-notes.md) | Deeper compare vs Cubical Agda / directed TT / homotopy.io / Catt |
| [docs/10-open-questions.md](docs/10-open-questions.md) | Follow-up research questions |
| [docs/sources.md](docs/sources.md) | Bibliography and dated links |
| [docs/appendix-cli-reference.md](docs/appendix-cli-reference.md) | CLI flags from `rzk/app/Main.hs` |

## Snapshot (research time)

- **Language:** Haskell (`Dependent Types` on Hackage), proof language `rzk-1`
- **Stars / forks (upstream):** ~301 / ~30 (GitHub metadata; may drift)
- **Primary formalizations:** [rzk-lang/sHoTT](https://github.com/rzk-lang/sHoTT), [emilyriehl/yoneda](https://github.com/emilyriehl/yoneda)
- **Maintainer / lead:** Nikolai Kudasov (`fizruk`) and collaborators listed in upstream `CONTRIBUTORS.md`
- **Citation style in these notes:** paraphrase + short quotes + URL/arXiv citations (「抄一下」= synthesize, do not paste long verbatim text)

## License of these notes

These notes are original English prose for research and learning. Upstream code and docs remain under their own licenses (Rzk package: BSD-3). Cite papers when you reuse mathematical claims.

**Last updated:** 2026-09-28 (Asia/Singapore, UTC+8) — Reddit discourse pass (sparse coverage documented).
