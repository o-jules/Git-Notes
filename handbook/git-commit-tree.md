# `git commit-tree`

Create a commit based on a explictly provided tree object. (may be used together with [`git write-tree`](git-write-tree.md] command).

## Synopsis

```bash
git commit-tree <tree> [(-p <parent>)...]

git commit-tree [(-p <parent>)...] [-S[ <keyid>]] [(-m <message>...)] [(-F <file>)...] <tree>
```

## Options

- `<tree>`: an existing tree object
- `-p <parent>`: id of parent commit object
- `-m <message>`: commit log message (more than one paragraphs)
- `-F <file>`: read commit log message from the given file; (more than on files)
- `-S[ <keyid>]`, `--gpg-sin[=<keyid>]`: GPG-sign commits
- `--no-gpg-sign`: do not GPG-sign commit
