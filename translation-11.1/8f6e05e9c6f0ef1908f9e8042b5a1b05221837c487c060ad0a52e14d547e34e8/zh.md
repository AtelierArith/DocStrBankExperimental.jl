```
conj(A::AbstractArray)
```

返回一个数组，其中包含数组 `A` 中每个条目的复共轭。

等价于 `conj.(A)`，但当 `eltype(A) <: Real` 时，`A` 会在不复制的情况下返回，并且当 `A` 具有零维时，返回一个零维数组（而不是标量）。

# 示例

```jldoctest
julia> conj([1, 2im, 3 + 4im])
3-element Vector{Complex{Int64}}:
 1 + 0im
 0 - 2im
 3 - 4im

julia> conj(fill(2 - im))
0-dimensional Array{Complex{Int64}, 0}:
2 + 1im
```
