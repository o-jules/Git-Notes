# Git 验证

和远程仓库通信不需要验证的方法有下面几种。

## SSH

```bash
git remote set-url origin git@github.com:[use-rname]/repo.git
```

## `netrc`

对于 `git` 1.7.10 及以上版本；编辑文件 `~/.netrc`（Mac/Linux）, `%HOME%\_netrc`（Windows），加入以下内容。

```ini
machine github.com
    login [user-name]
    password [password]
```

## Git credential storage

Helper to store credentials on disk.
Using this helper will store your passwords unencrypted on disk, protected only by filesystem permissions.

- Enable in Git repository:

  ```bash
  git config credential.helper store
  ```

- Enable globally:

  ```bash
  git config --global credential.helper store
  ```

- Edit `.git-credentials` file (plaintext)

  Each credential is stored on its own line as a URL like:
  ```
  https://user:pass@example.com
  ```

## Git credential cache

Similiar to Git credential store, but works temporally in memory.

```bash
git config credential.helper cache

# in 5 minutes (300 seconds)
git config credential.helper 'cache --timeout=300'
```
