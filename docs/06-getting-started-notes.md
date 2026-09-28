# Getting started notes (newcomer path)

Practical sequence distilled from upstream getting-started docs, plus research-oriented tips.

## 0. Decide how you will run the checker

| Goal | Path |
|------|------|
| Try 20 lines once | [Playground](https://rzk-lang.github.io/rzk/develop/playground/) |
| Learn by filling holes | [Warm-up Game](https://rzk-lang.github.io/warmup-game/) then [∞-Yoneda Game](https://rzk-lang.github.io/yoneda-game/) |
| Real editing | VS Code + [rzk extension](https://marketplace.visualstudio.com/items?itemName=NikolaiKudasovfizruk.rzk-1-experimental-highlighting) |
| Library work / CI | Local `rzk` binary (Release, Hackage, or `develop` build) |

## 1. Minimal literate file

Save as `example.rzk.md`:

````markdown
# Sample

```rzk
#lang rzk-1

#define id (A : U)
  : A -> A
  := \x -> x
```
````

```sh
rzk typecheck example.rzk.md
# expect: Everything is ok!
```

Language pragma `#lang rzk-1` is mandatory for the current surface language.

## 2. Learn the layers in order

1. MLTT fragment: functions, Σ, identity, `idJ` — `getting-started/dependent-types.rzk.md`, `reference/type-layer.rzk.md`
2. Cubes `CUBE` / directed interval `2` — `reference/cube-layer.rzk.md`
3. Topes `TOPE` — `reference/tope-layer.rzk.md`
4. Extension / shape-restricted types — `reference/extension-types.rzk.md`
5. Only then: Segal-style hom reasoning in libraries (read yoneda/sHoTT sources alongside the paper)

## 3. Start a multi-file project

- Clone [rzk-project-template](https://github.com/rzk-lang/rzk-project-template) or mirror sHoTT layout.
- Add `rzk.yaml` with an `include:` list.
- Name files so lexicographic order matches dependency order (`00-prelude.rzk.md`, `01-…`).
- CI: use [rzk-action](https://github.com/rzk-lang/rzk-action).

```sh
rzk typecheck 0-*.md 1-*.md
rzk format --check
```

## 4. Read mathematics and formalization together

- Paper: [arXiv:1705.07442](https://arxiv.org/abs/1705.07442) (shapes, extension types, Segal/Rezk).
- Formalized Yoneda story: [arXiv:2309.08340](https://arxiv.org/abs/2309.08340) + https://emilyriehl.github.io/yoneda/
- Broader library: https://rzk-lang.github.io/sHoTT/

## 5. When stuck

- Zulip: https://rzk-lang.zulipchat.com/register/
- `rzk typecheck --allow-holes` to inspect goals (also how games work).
- `rzk typecheck --json` for editor/tooling integration.
- Ask whether the failure is a **tope** obligation vs a **type** mismatch—error rendering walks scoped contexts (`ppTypeErrorInScopedContext` in Main).

## 6. Optional: build from source

Only if you need `develop` fixes or want to contribute:

```sh
git clone https://github.com/rzk-lang/rzk.git
cd rzk && git checkout develop
stack build && stack install
stack test
```

For Nix users, follow upstream README “Develop with nix” (flakes + direnv recommended).

## Research-oriented tip

If your goal is understanding *design*, skim in this order: paper §§1–2 (shapes & extension types) → Rzk `reference/introduction` → `Language/Rzk/Foil/Syntax.hs` header comments → `Rzk/TypeCheck.hs` module split → sHoTT root `rzk.yaml` / early numbered files. That path connects math, surface language, and implementation faster than reading the entire MkDocs tree linearly.
