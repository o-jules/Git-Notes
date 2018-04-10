# Git 历史管理

## 撤消

1. `git revert`:

   撤销某次 commit，该次 commit 之前的 commit 都会被保留，并生成新的 commit。
   例如：`git revert COMMIT_HASH`，在该COMMIT_HASH 的 commit下添加了文件A，在revert之后，文件A将从硬盘上消失。

2. `git reset`:

   回到某 commit，该次及之前的 commit 都会被保留，但是此次之后的修改都会被退回到暂存区(如果加上参数 `--hard`，则此后的所有修改将被抺除)。

### 示例

1. 撤消commit（未push远程）

```bash
# 取消最近一次commit，修改保留
git reset --soft HEAD~1

# 取消最近的2次commit，并保留修改
git reset --soft HEAD~2

# 取消最近一次commit，所有的修改都会被取消（硬盘数据不保留）
git reset --hard HEAD~1
```

## 附录

  - [git revert 命令帮助](https://git-scm.com/docs/git-revert)
  - [git reset 命令帮助](https://git-scm.com/docs/git-reset)
