```
accumulate!(op, B, A; [dims], [init])
```

Operación acumulativa `op` sobre `A` a lo largo de la dimensión `dims`, almacenando el resultado en `B`. Proporcionar `dims` es opcional para vectores. Si se proporciona el argumento clave `init`, su valor se utiliza para instanciar la acumulación.

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.


Véase también [`accumulate`](@ref), [`cumsum!`](@ref), [`cumprod!`](@ref).

# Ejemplos

```jldoctest
julia> x = [1, 0, 2, 0, 3];

julia> y = rand(5);

julia> accumulate!(+, y, x);

julia> y
5-element Vector{Float64}:
 1.0
 1.0
 3.0
 3.0
 6.0

julia> A = [1 2 3; 4 5 6];

julia> B = similar(A);

julia> accumulate!(-, B, A, dims=1)
2×3 Matrix{Int64}:
  1   2   3
 -3  -3  -3

julia> accumulate!(*, B, A, dims=2, init=10)
2×3 Matrix{Int64}:
 10   20    60
 40  200  1200
```
