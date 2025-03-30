```
Bidiagonal(A, uplo::Symbol)
```

`A`'n ana diyagonalından ve ilk süper (eğer `uplo=:U`) veya alt diyagonalından (eğer `uplo=:L`) bir `Bidiagonal` matris oluşturur.

# Örnekler

```jldoctest
julia> A = [1 1 1 1; 2 2 2 2; 3 3 3 3; 4 4 4 4]
4×4 Matrix{Int64}:
 1  1  1  1
 2  2  2  2
 3  3  3  3
 4  4  4  4

julia> Bidiagonal(A, :U) # A'nın ana diyagonalını ve ilk süper diyagonalını içerir
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  1  ⋅  ⋅
 ⋅  2  2  ⋅
 ⋅  ⋅  3  3
 ⋅  ⋅  ⋅  4

julia> Bidiagonal(A, :L) # A'nın ana diyagonalını ve ilk alt diyagonalını içerir
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  ⋅  ⋅  ⋅
 2  2  ⋅  ⋅
 ⋅  3  3  ⋅
 ⋅  ⋅  4  4
```
