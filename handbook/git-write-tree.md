# `git write-tree`

Create a tree object from current index.

*Tips*: In order to make things right, you may need to have done a `git update-index` phase before call `git write-tree`.

## When to use

Maybe when the use want to create a dangling tree object(e.g. to be used as the start point of a dangling commit).

