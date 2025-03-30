```
deleteat!(a::Vector, i::Integer)
```

删除给定 `i` 处的项并返回修改后的 `a`。后续项会被移动以填补结果中的空缺。

另见: [`keepat!`](@ref), [`delete!`](@ref), [`popat!`](@ref), [`splice!`](@ref)。

# 示例

```jldoctest
julia> deleteat!([6, 5, 4, 3, 2, 1], 2)
5-element Vector{Int64}:
 6
 4
 3
 2
 1
```
