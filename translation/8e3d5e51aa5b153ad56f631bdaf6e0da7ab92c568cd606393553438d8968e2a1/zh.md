```
popat!(a::Vector, i::Integer, [default])
```

移除给定 `i` 的项并返回它。后续项会被移动以填补结果间隙。当 `i` 不是 `a` 的有效索引时，返回 `default`，如果未指定 `default` 则抛出错误。

另请参见: [`pop!`](@ref), [`popfirst!`](@ref), [`deleteat!`](@ref), [`splice!`](@ref).

!!! compat "Julia 1.5"
    此函数自 Julia 1.5 起可用。


# 示例

```jldoctest
julia> a = [4, 3, 2, 1]; popat!(a, 2)
3

julia> a
3-element Vector{Int64}:
 4
 2
 1

julia> popat!(a, 4, missing)
missing

julia> popat!(a, 4)
ERROR: BoundsError: attempt to access 3-element Vector{Int64} at index [4]
[...]
```
