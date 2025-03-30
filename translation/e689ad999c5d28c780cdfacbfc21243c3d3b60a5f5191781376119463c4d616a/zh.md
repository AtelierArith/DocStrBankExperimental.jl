```
latex([io::IO], md)
```

输出Markdown对象`md`的内容为LaTeX格式，可以选择写入（可选的）`io`流或返回一个字符串。

也可以使用`show(io, "text/latex", md)`或`repr("text/latex", md)`。

# 示例

```jldoctest
julia> latex(md"hello _world_")
"hello \\emph{world}\n\n"
```
