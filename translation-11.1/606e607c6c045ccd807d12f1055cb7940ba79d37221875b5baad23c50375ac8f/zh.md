```
ncodeunits(s::AbstractString) -> Int
```

返回字符串中的代码单元数量。访问此字符串的有效索引必须满足 `1 ≤ i ≤ ncodeunits(s)`。并非所有这样的索引都是有效的——它们可能不是字符的开始，但在调用 `codeunit(s,i)` 时会返回一个代码单元值。

# 示例

```jldoctest
julia> ncodeunits("The Julia Language")
18

julia> ncodeunits("∫eˣ")
6

julia> ncodeunits('∫'), ncodeunits('e'), ncodeunits('ˣ')
(3, 1, 2)
```

另请参见 [`codeunit`](@ref), [`checkbounds`](@ref), [`sizeof`](@ref), [`length`](@ref), [`lastindex`](@ref).
