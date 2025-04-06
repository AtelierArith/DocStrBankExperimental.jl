```
sparsevec(d::Dict, [m])
```

Crée un vecteur creux de longueur `m` où les indices non nuls sont des clés du dictionnaire, et les valeurs non nulles sont les valeurs du dictionnaire.

# Exemples

```jldoctest
julia> sparsevec(Dict(1 => 3, 2 => 2))
2-element SparseVector{Int64, Int64} with 2 stored entries:
  [1]  =  3
  [2]  =  2
```
