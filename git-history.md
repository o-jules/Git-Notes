# Git历史管理

## 撤消

1. `git revert`:

   撤销某commit，该次commit之前的commit都会被保留，并生成新的commit。
   例如：`git revert COMMIT_HASH`，在该commit下添加了文件A，在revert之后，文件A将从硬盘上消失。

2. `git reset`:

   回到某commit，该次及之前的commit都会被保留，但是此次之后的修改都会被退回到暂存区(如果加上--hard，则修改将取消)。

### 示例：

1. 撤消commit（未push远程）

```bash
# 取消最近一次commit，修改保留
git reset --soft HEAD~1

# 取消最近的 2次commit，并保留修改
git reset --soft HEAD~2

# 取消最近一次commit，所有的修改都会被取消（硬盘数据不保留）
git reset --hard HEAD~1
```
