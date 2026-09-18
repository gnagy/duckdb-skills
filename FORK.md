# This fork

`gnagy/duckdb-skills` is a fork of [duckdb/duckdb-skills](https://github.com/duckdb/duckdb-skills),
kept to fix bugs found while using the plugin and to install it locally while those fixes are not
upstream. The plugin, its skills and their names are upstream's; nothing here restructures them.

## Branches

- `main`: upstream's `main`, the fix branches merged in, plus the fork-only files below.
- `fix/*`: one fix each, branched from `upstream/main` and carrying nothing fork-only, so each can
  be offered upstream as a pull request unchanged.

| Branch                    | Fixes                                                                                             |
|---------------------------|---------------------------------------------------------------------------------------------------|
| `fix/query-sandbox`       | Ad-hoc sandbox: `.duckdb` needs its `.wal`, extensions cannot autoload, globs are not paths (#17) |
| `fix/read-file-databases` | `read_any` on SQLite fails at bind time; `.duckdb` fell through to `read_blob`                    |
| `fix/docs-version-filter` | The docs + blog advice still searched `version = 'stable'`, which the index does not hold         |

To take upstream changes: `git fetch upstream && git merge upstream/main` on `main`.

## Fork-only files

- `FORK.md`: this file.
- `scripts/install`: copies the working copy into `~/.claude/skills/duckdb-skills`, where Claude
  Code loads it as `duckdb-skills@skills-dir`. Run it after every change you want sessions to see.
  It refuses while a marketplace install of `duckdb-skills` exists, which would load beside it.

`.claude-plugin/` is left as upstream has it, so upstream merges stay clean.
