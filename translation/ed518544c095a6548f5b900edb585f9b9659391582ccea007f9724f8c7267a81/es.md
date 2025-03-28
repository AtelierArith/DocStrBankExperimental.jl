```
sparsevec(I, V, [m, combine])
```

Crea un vector disperso `S` de longitud `m` tal que `S[I[k]] = V[k]`. Los duplicados se combinan utilizando la función `combine`, que por defecto es `+` si no se proporciona un argumento `combine`, a menos que los elementos de `V` sean Booleanos, en cuyo caso `combine` por defecto es `|`.

# Ejemplos

```jldoctest
julia> II = [1, 3, 3, 5]; V = [0.1, 0.2, 0.3, 0.2];

julia> sparsevec(II, V)
5-element SparseVector{Float64, Int64} with 3 stored entries:
  [1]  =  0.1
  [3]  =  0.5
  [5]  =  0.2

julia> sparsevec(II, V, 8, -)
8-element SparseVector{Float64, Int64} with 3 stored entries:
  [1]  =  0.1
  [3]  =  -0.1
  [5]  =  0.2

julia> sparsevec([1, 3, 1, 2, 2], [true, true, false, false, false])
3-element SparseVector{Bool, Int64} with 3 stored entries:
  [1]  =  1
  [2]  =  0
  [3]  =  1
```
