# Ecosystem

## Core project

| Resource | URL |
|----------|-----|
| Source | https://github.com/rzk-lang/rzk |
| Docs | https://rzk-lang.github.io/rzk/ |
| Org site | https://rzk-lang.github.io |
| Hackage | http://hackage.haskell.org/package/rzk |
| Stackage | badges in upstream README (Nightly / LTS) |
| Haddock (develop) | https://rzk-lang.github.io/rzk/haddock/index.html |
| Zulip | https://rzk-lang.zulipchat.com |

## Formalization libraries

### sHoTT (`rzk-lang/sHoTT`)

- **Focus:** simplicial HoTT and synthetic ∞-categories; expanding coverage beyond the original yoneda fork
- **Docs:** https://rzk-lang.github.io/sHoTT/
- **Repo:** https://github.com/rzk-lang/sHoTT (~72★ at survey)
- **Modal / directed univalence:** experimental work on branch `diruniv` (LIshy2 fork/branch referenced from Rzk modalities docs)

Checking sHoTT is the de facto performance regression corpus for the Haskell RTS flags and free-foil bumps.

### yoneda (`emilyriehl/yoneda`)

- **Focus:** comparative formalizations of the Yoneda lemma (1-categories vs ∞-categories)
- **Docs:** http://emilyriehl.github.io/yoneda/
- **Repo:** https://github.com/emilyriehl/yoneda (~82★)
- **Paper:** Kudasov, Riehl, Weinberger — *Formalizing the ∞-categorical Yoneda lemma*, [arXiv:2309.08340](https://arxiv.org/abs/2309.08340)
- **Geodesic path:** e.g. `simplicial-hott/13-yoneda-geodesic.rzk` (also powering the ∞-Yoneda Game)

### hottbook

Upstream index mentions efforts to formalize the HoTT Book in Rzk: https://rzk-lang.github.io/hottbook/

## Editor and language tools

| Tool | Role |
|------|------|
| [rzk-lang/vscode-rzk](https://github.com/rzk-lang/vscode-rzk) | Primary editor UX; semantic highlighting via LSP |
| Built-in `rzk lsp` / `rzk format` | Server + formatter (Agda-unimath–inspired style used in yoneda/sHoTT) |
| [rzk-lang/pygments-rzk](https://github.com/rzk-lang/pygments-rzk) | Pygments lexer for MkDocs / LaTeX minted |
| [rzk-lang/mkdocs-plugin-rzk](https://github.com/rzk-lang/mkdocs-plugin-rzk) | Literate-doc enhancements |
| [rzk-lang/rzk-action](https://github.com/rzk-lang/rzk-action) | CI typecheck/format for Rzk projects |
| [rzk-lang/rzk-project-template](https://github.com/rzk-lang/rzk-project-template) | Starter multi-file project |

## Games and learning surfaces

| Project | URL |
|---------|-----|
| rzk-game engine | https://github.com/rzk-lang/rzk-game |
| Game template | https://github.com/rzk-lang/rzk-game-template |
| Warm-up Game | https://rzk-lang.github.io/warmup-game/ |
| ∞-Yoneda Game | https://rzk-lang.github.io/yoneda-game/ |
| Playground | https://rzk-lang.github.io/rzk/latest/playground/ |

Games compile the checker to WASM/JS; players fill `?` holes and see goals/contexts—no local Haskell install.

## Research / sibling repositories

| Repo | Role |
|------|------|
| [fizruk/simple-topes](https://github.com/fizruk/simple-topes) | Standalone tope-layer prover; user-defined cubes/topes/axioms; intended merge into Rzk when stable (expands beyond fixed RSTT shape theory toward cubical/globular variants) |
| [fizruk/free-foil](https://github.com/fizruk/free-foil) | Binder/substitution library used by Rzk |
| E-unification paper code / ideas | arXiv:2302.05815 — future dependent inference direction |

## Comparison landscape (brief)

Upstream `docs/docs/en/related.md` situates Rzk among Agda / Cubical Agda, Arend, Aya, redtt/cooltt, Coq-HoTT/UniMath, Lean (historical HoTT / Ground Zero). Rzk’s differentiator is **RSTT shapes + extension types + tope solver** aimed at synthetic ∞-categories, not a maximal cubical HIT toolkit.

## Contributors (upstream list)

From `CONTRIBUTORS.md`: Nikolai Kudasov; Abdelrahman Abounegm (LSP); Danila Danko (Nix, playground); Ekaterina Maximova (tuple patterns, LSP tokenization, nested Σ sugar); Islam Talipov (modal TTT extension, `let`-bindings).
