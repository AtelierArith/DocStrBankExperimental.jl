```
selectdim(A, d::Integer, i)
```

Gibt eine Ansicht aller Daten von `A` zurück, bei denen der Index für die Dimension `d` gleich `i` ist.

Entspricht `view(A,:,:,...,i,:,:,...)`, wobei `i` an der Position `d` steht.

Siehe auch: [`eachslice`](@ref).

# Beispiele

```jldoctest
julia> A = [1 2 3 4; 5 6 7 8]
2×4 Matrix{Int64}:
 1  2  3  4
 5  6  7  8

julia> selectdim(A, 2, 3)
2-element view(::Matrix{Int64}, :, 3) with eltype Int64:
 3
 7

julia> selectdim(A, 2, 3:4)
2×2 view(::Matrix{Int64}, :, 3:4) with eltype Int64:
 3  4
 7  8
```
