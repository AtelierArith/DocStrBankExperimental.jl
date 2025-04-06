```
Bidiagonal(A, uplo::Symbol)
```

Construit une matrice `Bidiagonal` à partir de la diagonale principale de `A` et de sa première super-diagonale (si `uplo=:U`) ou sous-diagonale (si `uplo=:L`).

# Exemples

```jldoctest
julia> A = [1 1 1 1; 2 2 2 2; 3 3 3 3; 4 4 4 4]
4×4 Matrix{Int64}:
 1  1  1  1
 2  2  2  2
 3  3  3  3
 4  4  4  4

julia> Bidiagonal(A, :U) # contient la diagonale principale et la première superdiagonale de A
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  1  ⋅  ⋅
 ⋅  2  2  ⋅
 ⋅  ⋅  3  3
 ⋅  ⋅  ⋅  4

julia> Bidiagonal(A, :L) # contient la diagonale principale et la première sous-diagonale de A
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  ⋅  ⋅  ⋅
 2  2  ⋅  ⋅
 ⋅  3  3  ⋅
 ⋅  ⋅  4  4
```
