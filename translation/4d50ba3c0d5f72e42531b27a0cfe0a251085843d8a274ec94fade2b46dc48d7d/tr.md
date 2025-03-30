```
selectdim(A, d::Integer, i)
```

`A`'nın `d` boyutu için indeksinin `i`'ye eşit olduğu tüm verilerin bir görünümünü döndürür.

`i`'nin `d` konumunda olduğu `view(A,:,:,...,i,:,:,...)` ile eşdeğerdir.

Ayrıca bkz: [`eachslice`](@ref).

# Örnekler

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
