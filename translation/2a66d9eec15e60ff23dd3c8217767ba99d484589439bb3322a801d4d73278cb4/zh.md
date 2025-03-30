```
graphemes(s::AbstractString, m:n) -> SubString
```

返回一个 [`SubString`](@ref)，它由字符串 `s` 的第 `m` 到第 `n` 个 graphemes 组成，其中第二个参数 `m:n` 是一个整数值的 [`AbstractUnitRange`](@ref)。

宽泛地说，这对应于字符串中的第 `m:n` 个用户感知的“字符”。例如：

```jldoctest
julia> s = graphemes("exposé", 3:6)
"posé"

julia> collect(s)
5-element Vector{Char}:
 'p': ASCII/Unicode U+0070 (category Ll: Letter, lowercase)
 'o': ASCII/Unicode U+006F (category Ll: Letter, lowercase)
 's': ASCII/Unicode U+0073 (category Ll: Letter, lowercase)
 'e': ASCII/Unicode U+0065 (category Ll: Letter, lowercase)
 '́': Unicode U+0301 (category Mn: Mark, nonspacing)
```

这由 `"exposé"` 中的第 3 到 *7* 个代码点 ([`Char`](@ref)s) 组成，因为 grapheme `"é"` 实际上是 *两个* Unicode 代码点（一个 `'e'` 后跟一个重音符号组合字符 U+0301）。

由于查找 grapheme 边界需要遍历字符串内容，因此 `graphemes(s, m:n)` 函数所需的时间与字符串的长度（代码点数量）成正比，直到子字符串的末尾。

!!! compat "Julia 1.9"
    `graphemes` 的 `m:n` 参数需要 Julia 1.9。

