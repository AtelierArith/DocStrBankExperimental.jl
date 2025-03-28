```
ntuple(f, n::Integer)
```

Crea una tupla de longitud `n`, computando cada elemento como `f(i)`, donde `i` es el índice del elemento.

# Ejemplos

```jldoctest
julia> ntuple(i -> 2*i, 4)
(2, 4, 6, 8)
```
