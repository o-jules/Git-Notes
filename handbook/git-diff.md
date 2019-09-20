# git diff

Show the difference between commits, paths, blobs, commit and working tree etc.

Usages samples:

- git diff [<options>] [--] [<path...>]

  diff relative to index(staging area for the next commit)
  
  ```bash
  git diff
  ```

- git diff [<options>] --no-index [--] <path> <path>

  compare 2 path on the filesystem.

For more information, see `git help diff`.

## Options

- `--name-only`: show file names only
- `--name-status`: show file names and status(A/added, M/modified, D/deleted etc) only 
- `--numstat`: show number of lines added and deleted
- `--summary`: show the summary of changes
- `--diff-algorithm={patience|minimal|histogram|myers}`: default myers

## Extra commands

- `git diff-tree`
- `git diff-index`

## Examples 

```bash
## diff current working tree to latest commit
git diff

git diff-tree <commit-hash>
```
