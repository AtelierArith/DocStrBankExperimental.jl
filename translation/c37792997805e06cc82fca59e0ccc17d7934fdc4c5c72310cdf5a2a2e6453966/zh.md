```
html([io::IO], md)
```

以 HTML 格式输出 Markdown 对象 `md` 的内容，可以选择写入一个（可选的）`io` 流或返回一个字符串。

可以选择使用 `show(io, "text/html", md)` 或 `repr("text/html", md)`，它们的不同之处在于将输出包装在 `<div class="markdown"> ... </div>` 元素中。

# 示例

```jldoctest
julia> html(md"hello _world_")
"<p>hello <em>world</em></p>\n"
```
