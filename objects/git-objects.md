# Git Objects

Object 是 Git 储存版本纪录的文件对象。

Git系统中总共有四类Objct，分类是 commit, tree, blob, tag。

  - commit object: 记录的是某个 commit
  - tree object: 记录的是某个目录
  - blob object: 记录的是某个文件
  - tag object: 记录的是某个 tag

## Object 的生成方法

### blob object

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

### tree object

### commit object

### tag object

