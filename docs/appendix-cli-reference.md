# Appendix: CLI reference (from `rzk/app/Main.hs`)

Derived from the `optparse-generic` command definitions in upstream `rzk/app/Main.hs` (package v0.11.3 lineage). The progdesc string is:

> `rzk: an experimental proof assistant for synthetic ∞-categories`

## `rzk typecheck`

**Usage:** `rzk typecheck [OPTIONS] [FILE...]`

Parses Rzk modules from the given paths, or from **stdin** if none are provided (`parseRzkFilesOrStdin`).

| Flag | Short | Effect |
|------|-------|--------|
| `--allow-holes` | `-H` | Do not fail solely because of unsolved holes; print each hole’s goal and local context. Still fails on type errors. |
| `--json` | `-j` | Emit diagnostics (type errors, warnings, holes) as a **JSON array on stdout**; progress on stderr. Exit non-zero iff any diagnostic has error severity. |

Default (no `-H`, no `-j`): `typecheckModules`; print warnings; on success print `Everything is ok!`; on error print a rendered type error and exit non-zero.

With `-H`: uses `typecheckModulesWithHoles`; success message includes hole count.

## `rzk format`

**Usage:** `rzk format [OPTIONS] [FILE...]`

Paths are expanded via `expandRzkPathsOrYaml` (globs / `rzk.yaml` when appropriate). Empty expansion → runtime error `No files found`.

| Flag | Short | Effect |
|------|-------|--------|
| `--check` | `-c` | Exit non-zero if any file is not well-formatted; print offending paths. |
| `--write` | `-w` | Overwrite files with formatted content. |

`--check` and `--write` are **mutually exclusive**.

If neither flag is set: print formatted content for each file to **stdout**.

## `rzk lsp`

Starts the language server (`Language.Rzk.VSCode.Lsp.runLsp`) when built with `LSP_ENABLED`. Otherwise the process errors: `rzk lsp is not supported with this build`.

## `rzk version`

| Flag | Short | Effect |
|------|-------|--------|
| *(none)* | | Print bare `versionString` (default — VS Code and tools scrape this). |
| `--full` | `-f` | Print commit, compiler, platform, LSP support (`ppVersionInfo`). |
| `--json` | `-j` | Print the same structured `versionInfo` record as JSON. |

Implementation note: version details come from `Rzk.Version` (gitrev at compile time when available; degrades to `UNKNOWN` in tarball/wasm contexts per `package.yaml` comments).

## Related non-CLI entry points

- Library API used by playground / games / WASM builds (via `rzk-js`), not covered by this argv surface.
- Project YAML schema: `include` (required), `exclude` (optional list) — `Rzk.Project.Config`.
