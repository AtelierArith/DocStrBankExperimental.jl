```
reverse(s::AbstractString) -> AbstractString
```

反转一个字符串。从技术上讲，这个函数反转字符串中的代码点，其主要用途是进行反向字符串处理，特别是反向正则表达式搜索。另请参见 [`reverseind`](@ref) 将 `s` 中的索引转换为 `reverse(s)` 中的索引，反之亦然，以及来自 `Unicode` 模块的 `graphemes`，以便对用户可见的“字符”（字形）而不是代码点进行操作。另请参见 [`Iterators.reverse`](@ref) 以无须复制的方式进行反向迭代。自定义字符串类型必须自行实现 `reverse` 函数，并通常应返回具有相同类型和编码的字符串。如果它们返回具有不同编码的字符串，则必须覆盖该字符串类型的 `reverseind` 以满足 `s[reverseind(s,i)] == reverse(s)[i]`。

# 示例

```jldoctest
julia> reverse("JuliaLang")
"gnaLailuJ"
```

!!! note
    下面的示例在不同系统上可能会呈现不同。注释指示它们应该如何呈现


组合字符可能会导致意外结果：

```jldoctest
julia> reverse("ax̂e") # 帽子在输入中位于 x 上方，在输出中位于 e 上方
"êxa"

julia> using Unicode

julia> join(reverse(collect(graphemes("ax̂e")))) # 反转字形；帽子在输入和输出中都位于 x 上方
"ex̂a"
```
