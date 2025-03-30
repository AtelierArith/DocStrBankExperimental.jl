```
map!(function, destination, collection...)
```

类似于 [`map`](@ref)，但将结果存储在 `destination` 中，而不是新的集合。`destination` 必须至少与最小的集合一样大。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


另请参见: [`map`](@ref), [`foreach`](@ref), [`zip`](@ref), [`copyto!`](@ref)。

# 示例

```jldoctest
julia> a = zeros(3);

julia> map!(x -> x * 2, a, [1, 2, 3]);

julia> a
3-element Vector{Float64}:
 2.0
 4.0
 6.0

julia> map!(+, zeros(Int, 5), 100:999, 1:3)
5-element Vector{Int64}:
 101
 103
 105
   0
   0
```
