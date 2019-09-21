# git tag

Git Tag 是一个静态的ref（即指针，引用），用于定位版本中的某一个资源（通常是一个commit）。

## 分类

Git Tag 分为两类，annotated tag 和 lightweight tag。
annotated tag 创建一个新的 tag object，lightweight tag 只是创建一个 ref。

Git Tag 储存在 `.git/refs/tags`，文件名是 tag名。
annotated tag 的 ref 文件是 tag object 的 hash；lightweight tag 的 ref 内容是指向的 tag 创建时的commit object 的 hash。

Git Tag Object 同其它 object 一样，储存在 `.git/objects` 下。其内容包括：

  - object：object 对象的 hash
  - type：object 的类型
  - tag：tag名
  - tagger：打tag人的名字及时间等信息
  - message：额外的信息

## tag 的用途

Tag 主要用来管理软件开发生命周期中的开发版本。

## `git tag` 命令

  - `-a`
    ```bash
    # lightweight tag
    git tag $tag_name
    git tag $tag_name $commit_hash

    # annotated tag point to current commit
    git tag -a $tag_name

    # annotated tag point to specific commit
    git tag -a $tag_name $commit_hash
    ```

  - `--list, -l` 显示 tag 的列表

  - `--delete,-d` 删除 tag

## 共享 tag

`git push`默认不会主动将 tag 推送到 Git 仓库，需要手动指定。

```bash
# push specific tag
git push origin $tag_name

# push all tags that are not in remote repository
git push origin --tags
```

## Viewing Tags

- Show tag list
  ```bash
  git tag --list
  ```

- Show hash of a tag
  ```bash
  git show-ref --tags <tagname>
  ```

- Show related info of tag (the tag itself and the commits it point to)
  ```bash
  git show <tag-name>
  ```

## Checkout

Tag is not a branch. You can only checkout new branch point to the tag's ref, or checkout a existed branch at the ref (usual a commit).
Otherwise you will have a detached HEAD.

```bash
git checkout -b <branch-name> <tag-name>
```
