```
nextind(A, i)
```

Devuelve el índice después de `i` en `A`. El índice devuelto a menudo es equivalente a `i + 1` para un entero `i`. Esta función puede ser útil para código genérico.

!!! warning
    El índice devuelto podría estar fuera de los límites. Considera usar [`checkbounds`](@ref).


Véase también: [`prevind`](@ref).

# Ejemplos

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> nextind(x, 1) # resultado válido
2

julia> nextind(x, 4) # resultado inválido
5

julia> nextind(x, CartesianIndex(1, 1)) # resultado válido
CartesianIndex(2, 1)

julia> nextind(x, CartesianIndex(2, 2)) # resultado inválido
CartesianIndex(1, 3)
```
