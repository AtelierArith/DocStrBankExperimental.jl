```
repeat(A::AbstractArray, counts::Integer...)
```

Konstruiere ein Array, indem das Array `A` eine gegebene Anzahl von Malen in jeder Dimension wiederholt wird, wie durch `counts` angegeben.

Siehe auch: [`fill`](@ref), [`Iterators.repeated`](@ref), [`Iterators.cycle`](@ref).

# Beispiele

```jldoctest
julia> repeat([1, 2, 3], 2)
6-element Vector{Int64}:
 1
 2
 3
 1
 2
 3

julia> repeat([1, 2, 3], 2, 3)
6×3 Matrix{Int64}:
 1  1  1
 2  2  2
 3  3  3
 1  1  1
 2  2  2
 3  3  3
```
