```
Tridiagonal(A)
```

Construit une matrice tridiagonale à partir de la première sous-diagonale, de la diagonale et de la première super-diagonale de la matrice `A`.

# Exemples

```jldoctest
julia> A = [1 2 3 4; 1 2 3 4; 1 2 3 4; 1 2 3 4]
4×4 Matrix{Int64}:
 1  2  3  4
 1  2  3  4
 1  2  3  4
 1  2  3  4

julia> Tridiagonal(A)
4×4 Tridiagonal{Int64, Vector{Int64}}:
 1  2  ⋅  ⋅
 1  2  3  ⋅
 ⋅  2  3  4
 ⋅  ⋅  3  4
```
