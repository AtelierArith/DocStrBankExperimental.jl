```
length(s::AbstractString) -> Int
length(s::AbstractString, i::Integer, j::Integer) -> Int
```

返回字符串 `s` 中从索引 `i` 到 `j` 的字符数量。

这被计算为从 `i` 到 `j` 的代码单元索引中有效字符索引的数量。仅使用单个字符串参数时，这将计算整个字符串中的字符数量。使用 `i` 和 `j` 参数时，它计算在字符串 `s` 中有效索引的 `i` 和 `j` 之间（包括 `i` 和 `j`）的索引数量。除了在范围内的值，`i` 可以取超出范围的值 `ncodeunits(s) + 1`，而 `j` 可以取超出范围的值 `0`。

!!! note
    此操作的时间复杂度通常是线性的。也就是说，它所需的时间与字符串中的字节或字符数量成正比，因为它是动态计数的。这与数组的方法形成对比，后者是常数时间操作。


另请参见 [`isvalid`](@ref), [`ncodeunits`](@ref), [`lastindex`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref)。

# 示例

```jldoctest
julia> length("jμΛIα")
5
```
