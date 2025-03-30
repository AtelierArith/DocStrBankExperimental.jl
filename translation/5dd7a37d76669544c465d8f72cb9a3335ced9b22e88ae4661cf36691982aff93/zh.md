```
apropos([io::IO=stdout], pattern::Union{AbstractString,Regex})
```

搜索可用的文档字符串，查找包含 `pattern` 的条目。

当 `pattern` 是一个字符串时，忽略大小写。结果将打印到 `io`。

可以通过在 REPL 的帮助模式中将查询用双引号括起来来调用 `apropos`：

```
help?> "pattern"
```
