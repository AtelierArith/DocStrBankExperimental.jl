```
isvalid(s::AbstractString, i::Integer) -> Bool
```

谓词指示给定索引是否是 `s` 中字符编码的起始位置。如果 `isvalid(s, i)` 为真，则 `s[i]` 将返回该索引处编码开始的字符；如果为假，则 `s[i]` 将引发无效索引错误或边界错误，具体取决于 `i` 是否在有效范围内。为了使 `isvalid(s, i)` 成为 O(1) 函数，`s` 的编码必须是 [自同步的](https://en.wikipedia.org/wiki/Self-synchronizing_code)。这是 Julia 通用字符串支持的基本假设。

另请参见 [`getindex`](@ref), [`iterate`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref), [`length`](@ref)。

# 示例

```jldoctest
julia> str = "αβγdef";

julia> isvalid(str, 1)
true

julia> str[1]
'α': Unicode U+03B1 (category Ll: Letter, lowercase)

julia> isvalid(str, 2)
false

julia> str[2]
ERROR: StringIndexError: invalid index [2], valid nearby indices [1]=>'α', [3]=>'β'
Stacktrace:
[...]
```
