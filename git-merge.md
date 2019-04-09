# git merge

`git merge` 用于合并分支，将两个及以上的开发历史记录合并在一起。

## 使用示例

```bash
# 假设当前在 master 分出，需要合并 dev 分支上的内容
# $BRANCH_NAME = dev
git merge $BRANCH_NAME

# 假设当前需要合并多个分支
git merge dev fixes
```

## 参数

  - `--commit`

    默认合并后会立即产生一个新的 commit。

  - `--no-commit`

    合并但不立即执行 commit 操作，可以给用户按需要二次修改再提交 commit。

  - `--edit`, `-e`

    在 commit 前打开文本编辑器，用户可以自定义 commit 的信息。

  - `--no-edit`

    在 commit 的时候使用自动生成的 commit 信息。

## 合并 tag
