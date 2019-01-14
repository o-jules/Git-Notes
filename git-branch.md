# Git分支

## 查看分支

### 查看现有分支

```bash
git branch
# 或者
git branch --list
```

### 查看远程分支

当 clone 一个远程项目时，`git branch --list` 不能直接查看到所有的远程分支。

```bash
git branch --remotes
git branch -r
```

### 查看所有分支

```bash
git branch --all
git branch -a
```

## 创建分支

```bash
git branch BRANCH_NAME

# 或者
# 创建并切换分支
git checkout -b BRANCH_NAME
```

## 删除分支

```bash
git branch --delete BRANCH_NAME
git branch -d BRANCH_NAME

# short for
# git branch --delete --force BRANCH_NAME
git branch -D BRANCH_NAME
```

## 切换分支

```bash
git checkout develop
```

## 重命名分支

### 重命名本地分支

```bash
git branch --move OLD_NAME NEW_NAME

git branch -m OLD_NAME NEW_NAME

# short for
# git branch --move --force OLD_NAME NEW_NAME
# 当只改变大小写等场合使用
git branch -M OLD_NAME NEW_NAME
```

### 同步重命名远程分支

```bash
# TODO:
```
