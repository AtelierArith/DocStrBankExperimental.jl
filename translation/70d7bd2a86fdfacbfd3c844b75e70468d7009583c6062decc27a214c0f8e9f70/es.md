```
prevind(A, i)
```

Devuelve el índice antes de `i` en `A`. El índice devuelto a menudo es equivalente a `i - 1` para un entero `i`. Esta función puede ser útil para código genérico.

!!! warning
    El índice devuelto podría estar fuera de límites. Considera usar [`checkbounds`](@ref).


Véase también: [`nextind`](@ref).

# Ejemplos

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> prevind(x, 4) # resultado válido
3

julia> prevind(x, 1) # resultado inválido
0

julia> prevind(x, CartesianIndex(2, 2)) # resultado válido
CartesianIndex(1, 2)

julia> prevind(x, CartesianIndex(1, 1)) # resultado inválido
CartesianIndex(2, 0)
```
