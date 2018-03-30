# Git 验证

和远程仓库通信不需要验证的方法有下面几种。

## SSH

```bash
git remote set-url origin git@github.com:[use-rname]/repo.git
```

## `netrc`

对于 `git` 1.7.10 及以上版本；编辑文件 `.netrc`（Mac/Linux）, `%HOME%\_netrc`（Windows），加入以下内容。

```ini
machine github.com
    login [user-name]
    password [password]
```
