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

## Git crendentials

Show all credential helpers:

```bash
git help -a | grep credential-

# show the manual
git help <helper-name>
```

### Git credential store

Helper to store credentials on disk.

*Attention*: Using this helper will store your passwords unencrypted on disk, protected only by filesystem permissions.

- Store the credential in a Git repository:

  ```bash
  git config credential.helper store

  git push
  # input user name and password; the your credentials are used automatically.
  ```

- Store the credential globally:

  ```bash
  git config --global credential.helper store
  ```

- Set up custom file path:

  ```bash
  git config credential.helper 'store --file=<path>'
  ```

The default path is `~/.git-credentials` and `$XDG_CONFIG_HOME/git/credentials`.

- `.git/config`

  Setting up the store helper, the `.git/config` file would have the content:

  ```ini
  [credential]
      helper = store
  ```

  If you want to setup the user name only, edit `.git/config`:

  ```ini
  [credential "https://<remote-repository>"]
      username = <your-name>
  ```

- `~/.git-credentials` file (plaintext), the default file for storing credentials.

  Each credential is stored on its own line as a *URL* like:
  ```
  https://user:pass@example.com
  ```

  *Attention*: if your password contains special charaters like WHITE SPACE, `!` etc.
  they will be encoded into escape sequences.

## Git credential cache

Similiar to Git credential store, but works temporally in memory.

```bash
git config credential.helper cache

# in 5 minutes (300 seconds)
git config credential.helper 'cache --timeout=300'
```
