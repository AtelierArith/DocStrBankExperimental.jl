```
real(A::AbstractArray)
```

返回一个数组，包含数组 `A` 中每个条目的实部。

等价于 `real.(A)`，但当 `eltype(A) <: Real` 时，`A` 会被直接返回而不进行复制，并且当 `A` 具有零维时，返回一个0维数组（而不是标量）。

# 示例

```jldoctest
julia> real([1, 2im, 3 + 4im])
3-element Vector{Int64}:
 1
 0
 3

julia> real(fill(2 - im))
0-dimensional Array{Int64, 0}:
2
```
