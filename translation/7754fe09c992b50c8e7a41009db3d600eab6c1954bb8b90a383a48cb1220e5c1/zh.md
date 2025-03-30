```
@md_str -> MD
```

解析给定的字符串作为Markdown文本，并返回相应的[`MD`](@ref)对象。

# 示例

```jldoctest
julia> s = md"# 你好，世界！"
  你好，世界！
  ≡≡≡≡≡≡≡≡≡≡≡≡≡

julia> typeof(s)
Markdown.MD

```
