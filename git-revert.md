# `git revert`

生成一个新的 commit，以取消旧历史某一个 commit 所作的修改。

## 使用示例

```bash
# 取消前一个 commit
git revert HEAD~1

# 取消某个 commit
git revert $COMMIT_HASH
```

## FAQ

- 如果需要被 revert 的 commit 中修改的内容，在后面的 commit 中又有改动，会如何？

因为文件会有冲突，不能直接产生一个新的 commit。此时会直接改动冲突的文件，需要手动修复并提交 commit。
