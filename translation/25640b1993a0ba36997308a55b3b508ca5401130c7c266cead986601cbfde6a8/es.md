```
sparsevec(d::Dict, [m])
```

Crea un vector disperso de longitud `m` donde los índices no nulos son claves del diccionario, y los valores no nulos son los valores del diccionario.

# Ejemplos

```jldoctest
julia> sparsevec(Dict(1 => 3, 2 => 2))
2-element SparseVector{Int64, Int64} with 2 stored entries:
  [1]  =  3
  [2]  =  2
```
