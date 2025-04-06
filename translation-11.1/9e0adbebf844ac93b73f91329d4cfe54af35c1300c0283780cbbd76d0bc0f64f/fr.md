```
findnz(A::SparseMatrixCSC)
```

Renvoie un tuple `(I, J, V)` où `I` et `J` sont les indices de ligne et de colonne des valeurs stockées ("non nulles structurellement") dans la matrice creuse `A`, et `V` est un vecteur des valeurs.

# Exemples

```jldoctest
julia> A = sparse([1 2 0; 0 0 3; 0 4 0])
3×3 SparseMatrixCSC{Int64, Int64} avec 4 entrées stockées :
 1  2  ⋅
 ⋅  ⋅  3
 ⋅  4  ⋅

julia> findnz(A)
([1, 1, 3, 2], [1, 2, 2, 3], [1, 2, 4, 3])
```
