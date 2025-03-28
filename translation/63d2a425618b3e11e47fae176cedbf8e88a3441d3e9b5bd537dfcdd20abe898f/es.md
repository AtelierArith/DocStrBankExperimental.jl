```
cumprod(A; dims::Integer)
```

Producto acumulativo a lo largo de la dimensión `dim`. Ver también [`cumprod!`](@ref) para usar un array de salida preasignado, tanto por rendimiento como para controlar la precisión de la salida (por ejemplo, para evitar desbordamientos).

# Ejemplos

```jldoctest
julia> a = Int8[1 2 3; 4 5 6];

julia> cumprod(a, dims=1)
2×3 Matrix{Int64}:
 1   2   3
 4  10  18

julia> cumprod(a, dims=2)
2×3 Matrix{Int64}:
 1   2    6
 4  20  120
```
