```
parent(A)
```

Retourne l'objet parent sous-jacent de la vue. Ce parent d'objets de types `SubArray`, `SubString`, `ReshapedArray` ou `LinearAlgebra.Transpose` est ce qui a été passé comme argument à `view`, `reshape`, `transpose`, etc. lors de la création de l'objet. Si l'entrée n'est pas un objet enveloppé, retourne l'entrée elle-même. Si l'entrée est enveloppée plusieurs fois, seule l'enveloppe la plus externe sera supprimée.

# Exemples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> V = view(A, 1:2, :)
2×2 view(::Matrix{Int64}, 1:2, :) with eltype Int64:
 1  2
 3  4

julia> parent(V)
2×2 Matrix{Int64}:
 1  2
 3  4
```
