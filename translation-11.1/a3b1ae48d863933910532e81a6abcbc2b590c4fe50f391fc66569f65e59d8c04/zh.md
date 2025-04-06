```
@doc_str -> MD

解析给定的字符串作为Markdown文本，添加行和模块信息，并返回相应的[`MD`](@ref)对象。

`@doc_str`可以与[`Base.Docs`](@ref)模块结合使用。有关更多信息，请参阅手册中的[文档](@ref man-documentation)部分。

# 示例

```

julia> s = doc"f(x) = 2*x"   f(x) = 2*x

julia> typeof(s) Markdown.MD

```
