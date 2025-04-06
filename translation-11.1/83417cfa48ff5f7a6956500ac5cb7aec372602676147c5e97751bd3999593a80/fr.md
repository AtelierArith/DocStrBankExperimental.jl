```
LinearAlgebra.checksquare(A)
```

Vérifiez qu'une matrice est carrée, puis renvoyez sa dimension commune. Pour plusieurs arguments, renvoyez un vecteur.

# Exemples

```jldoctest
julia> A = fill(1, (4,4)); B = fill(1, (5,5));

julia> LinearAlgebra.checksquare(A, B)
2-element Vector{Int64}:
 4
 5
```
