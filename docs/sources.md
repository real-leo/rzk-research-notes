# Sources and bibliography

Dates are publication or release dates where known. Links accessed during research on **2026-09-28** (Asia/Singapore).

## Foundational papers

1. Emily Riehl & Michael Shulman. *A type theory for synthetic ∞-categories*. Higher Structures 1(1), 147–224, **2017**.  
   https://arxiv.org/abs/1705.07442  
   (Corrected post-publication v5 acknowledges typos noted by Cnossen, Kudasov, Licata, Sattler.)

2. Nikolai Kudasov, Emily Riehl, Jonathan Weinberger. *Formalizing the ∞-categorical Yoneda lemma*. **2023**.  
   https://arxiv.org/abs/2309.08340

3. Nikolai Kudasov. *Functional Pearl: Dependent type inference via free higher-order unification*. **2022**.  
   https://arxiv.org/abs/2204.05653

4. Nikolai Kudasov. *E-Unification for Second-Order Abstract Syntax*. FSCD 2023, LIPIcs 260.  
   https://doi.org/10.4230/LIPIcs.FSCD.2023.10 · https://arxiv.org/abs/2302.05815

5. Nikolai Kudasov. *Experimental prover for Tope logic*. SCAN 2023, pp. 37–39.  
   https://www.mathnet.ru/ConfLogos/2220/abstracts.pdf#page=38

## Modal / TTT background (as cited by Rzk docs)

- Gratzer, Weinberger, Buchholtz — Triangulated Type Theory (see Rzk `reference/modalities.rzk.md` footnotes for the precise bibliographic pointers used upstream).

## Upstream software (survey snapshot)

| Artifact | Location | Notes |
|----------|----------|-------|
| Rzk source | https://github.com/rzk-lang/rzk | Default branch `develop`; BSD-3 package license |
| Release v0.11.3 | https://github.com/rzk-lang/rzk/releases/tag/v0.11.3 | **2026-08-31** |
| CITATION.cff | repo root | version 0.11.3, date-released 2026-08-31 |
| MkDocs English docs | https://rzk-lang.github.io/rzk/ | Built from `docs/docs/en/` |
| Hackage | http://hackage.haskell.org/package/rzk | |
| sHoTT | https://github.com/rzk-lang/sHoTT | |
| yoneda | https://github.com/emilyriehl/yoneda | |
| vscode-rzk | https://github.com/rzk-lang/vscode-rzk | |
| rzk-game | https://github.com/rzk-lang/rzk-game | |
| simple-topes | https://github.com/fizruk/simple-topes | |
| free-foil | https://github.com/fizruk/free-foil | v0.4.x used by Rzk |
| Zulip | https://rzk-lang.zulipchat.com | |

## Local research checkout

- Path: `/workspace/rzk-analysis/rzk` (shallow/full clone of `rzk-lang/rzk` on `develop`)
- Commit observed at research start: `01b081e` (*Merge pull request #362 from rzk-lang/warn-tope-family-domain*) — tip may move; version identity for notes is **v0.11.3** + develop docs/code read on 2026-09-28.

## Key in-repo paths consulted

- `README.md`, `CONTRIBUTORS.md`, `CITATION.cff`, `rzk.yaml`
- `rzk/package.yaml`, `rzk/app/Main.hs`, `rzk/ChangeLog.md`
- `rzk/src/Rzk/TypeCheck/**`, `rzk/src/Language/Rzk/Foil/**`, `rzk/src/Rzk/Project/Config.hs`
- `docs/docs/en/index.md`, `related.md`, `tools.md`, `community.md`, `getting-started/**`, `reference/**`
- `.github/workflows/*.yml`, `stack.yaml`, `cabal.project`, `flake.nix`
