```
maximum!(r, A)
```

Calcula el valor máximo de `A` sobre las dimensiones singleton de `r`, y escribe los resultados en `r`.

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.


# Ejemplos

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> maximum!([1; 1], A)
2-element Vector{Int64}:
 2
 4

julia> maximum!([1 1], A)
1×2 Matrix{Int64}:
 3  4
```
