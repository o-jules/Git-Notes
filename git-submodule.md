# Git 子模块

## 添加子模块

```bash
git submodule add REPOSITORY_URL LOCAL_PATH
```
（注意：LOCAL_PATH 不能以 `/` 结尾，也不能是当前工程已有的目录）

## 查看状态

```bash
git submodule status
```

## 批量操作

`git submodule foreach`

## 更新子模块

1. clone 主项目时更新：

```bash
git clone --recurse-submodules REPOSITORY_URL
```

2. clone 后更新：

```bash
git submodule init
git submodule update
```

或者：

```bash
git submodule update --init --recursive
```

## `.gitmodules` 文件

文件内容格式为：

```
[submodule "MODULE_NAME"]
	path = MODULE_PATH
	url = GIT_URL

```
