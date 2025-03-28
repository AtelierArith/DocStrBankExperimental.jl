```
BoundsError([a],[i])
```

Una operación de indexación en un arreglo, `a`, intentó acceder a un elemento fuera de los límites en el índice `i`.

# Ejemplos

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> A = fill(1.0, 7);

julia> A[8]
ERROR: BoundsError: intento de acceder a un Vector{Float64} de 7 elementos en el índice [8]


julia> B = fill(1.0, (2,3));

julia> B[2, 4]
ERROR: BoundsError: intento de acceder a una Matriz{Float64} de 2×3 en el índice [2, 4]


julia> B[9]
ERROR: BoundsError: intento de acceder a una Matriz{Float64} de 2×3 en el índice [9]

```
