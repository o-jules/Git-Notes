# Git Objects

Object 是 Git 储存版本纪录的文件对象。

Git系统中总共有四类Objct，分类是 commit, tree, blob, tag。

  - commit object: 记录的是某个 commit
  - tree object: 记录的是某个目录
  - blob object: 记录的是某个文件
  - tag object: 记录的是某个 tag

## object 的内容格式

### blob object

`blob [content-size]\0[content]`

其中，content-size 是 content 的字节数。

### tree object

`tree [content-size]\0[content]`

其中，content 是目录下的文件或者目录按字母表排序的条目，每条的格式为：

`[mode] [name]\0[hash-bytes]`

需要注意的是：

- `mode` 假如：目录为 40000，文件为 100644（其中，644是文件的权限设置）
  可以关闭：`git config core.filemode false`

- `name` 文件或者目录名
- `hash` 20个字节，hash的二进制格式（注意：不是字符串格式！）

### commit object

`commit [content-size]\0[content]`

其中 content 的格式为：

```
tree [tree-hash]
parent [tree-hash]
author [author-name] <[author-email]> [timestamp] [time-zone]
committer [committer-name] <[committer-email]> [timestamp] [time-zone]

[commit-message]
```

### tag object

`tag [tag-size]\0[content]`

其中 content 的格式为：

```
object [object-hash]
type [object-type]
tag [tag-name]
tagger [tagger-name] <[tagger-email]> [timestamp] [timezone]

[tag-message]
```

**object-type 一般是 commit**

## 示例：blob object 的生成方法

blob object 的 store 内容：

```ts
function blobStore(content: byte[]): byte[] {
  const header = `blob ${content.length}\0`;
  return header + content;
}
```

blob object 的 hash （文件名）计算:

```ts
function blobHash(content: byte[]): byte[] {
  return sha1.hexdigest(blobStore(content));
}
```

blob object 的文件内容的计算：

```ts
function blobFile(content: byte[]): byte[] {
  return zlib.deflate(blobStore(content));
}
```

## 命令行中查看 git object 原始格式（解压后）

```bash
# gzip tricks
printf "\x1f\x8b\x08\x00\x00\x00\x00\x00" | cat - .git/objects/$hash | gzip -dc | xxd

# pigz; installation requird
cat .git/objects/8a/44ce04ea77c7eccf9d6987eb8bfbe7b360209f | unpigz -c | xxd

## openssl; no built-in zlib for openssl in macOS
cat .git/objects/8a/44ce04ea77c7eccf9d6987eb8bfbe7b360209f | openssl zlib -d | xxd
```
