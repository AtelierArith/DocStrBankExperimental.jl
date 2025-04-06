```
stride(A, k::Integer)
```

Devuelve la distancia en memoria (en número de elementos) entre elementos adyacentes en la dimensión `k`.

Véase también: [`strides`](@ref).

# Ejemplos

```jldoctest
julia> A = fill(1, (3,4,5));

julia> stride(A,2)
3

julia> stride(A,3)
12
```
