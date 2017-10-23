# `gitignore`

`gitignore` 声明了当前未跟踪的文件中，哪些将被忽略；已跟踪的文件不会受影响。

用户可以在多处声明`gitignore`，其优先级从高到低排列如下：

  - 使用命令行工具时的参数
  - 与文件处于同一路径下的 `.gitignore` 文件
  - 文件的父目录中的 `.gitignore` 文件
  - 工程根目录的 `.gitignore` 文件
  - `$GIT_DIR/info/exclude`
  - 配置参数 `core.excludesFile` 指定的文件

## 规则

其中的文件声明分为黑名单声明与白名单声明。

以 `!` 开头的规则为白名单，其它为黑名单。以下是其它符号的含义：
  - `/` 表示目录
  - `*` 通配多个字符
  - `?` 通配单个字符
  - `[]` 包含单个字符的匹配列表

使用 U 表示所有文件的集合，则其作用规则为：

```typescript
function includes(rule_list: [Set]): Set {
  let excludes : Set = EMPTY_SET

  rule_list.forEach(r => {
    if (rule.isBlackList())
      excludes.union(rule)
    else
      excludes.minus(rule)
  })

  return U.minus(excludes)
}
```

# 相关命令

  - `git ls-files` 列出当前已跟踪的文件
  - `git status` 列出当前未跟踪（需要跟踪）的文件（更改）

# 参考资料

  - [gitignore](https://git-scm.com/docs/gitignore)
