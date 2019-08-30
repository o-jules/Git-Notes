# Git 配置

## 如何查看查看设置

```bash
# 查看所有的设置（含全局及本地）
git config --list

# 查看全局设置
git config --list --global

# 查看本地设置
git config --list --local
```

## 如何查看及设置当前的用户

```bash
## 以下为本地设置：

# 查看当前用户名
git config user.name
# 查看当前用户邮箱
git config user.email

# 设置当前用户名
git config user.name "NAME"
# 设置当前用户邮箱
git config user.email "E-MAIL"


## 如果需要设置全局，则需要加上`--global`标签：

git config --global user.name
git config --global user.name "NAME"
```

## 备注

除了使用git命令进行设置外，还可以编辑本地的`.git`目录下的config文件（该文件格式与`.ini`文件相近）。
