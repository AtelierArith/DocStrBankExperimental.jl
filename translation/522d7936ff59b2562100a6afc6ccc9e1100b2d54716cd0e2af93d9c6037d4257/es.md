```
accumulate(op, A; dims::Integer, [init])
```

Operación acumulativa `op` a lo largo de la dimensión `dims` de `A` (siempre que `dims` sea opcional para vectores). Un valor inicial `init` puede ser proporcionado opcionalmente mediante un argumento de palabra clave. Véase también [`accumulate!`](@ref) para usar un array de salida preasignado, tanto por rendimiento como para controlar la precisión de la salida (por ejemplo, para evitar desbordamientos).

Para operaciones comunes hay variantes especializadas de `accumulate`, consulte [`cumsum`](@ref), [`cumprod`](@ref). Para una versión perezosa, consulte [`Iterators.accumulate`](@ref).

!!! compat "Julia 1.5"
    `accumulate` en un iterador no-array requiere al menos Julia 1.5.


# Ejemplos

```jldoctest
julia> accumulate(+, [1,2,3])
3-element Vector{Int64}:
 1
 3
 6

julia> accumulate(min, (1, -2, 3, -4, 5), init=0)
(0, -2, -2, -4, -4)

julia> accumulate(/, (2, 4, Inf), init=100)
(50.0, 12.5, 0.0)

julia> accumulate(=>, i^2 for i in 1:3)
3-element Vector{Any}:
          1
        1 => 4
 (1 => 4) => 9

julia> accumulate(+, fill(1, 3, 4))
3×4 Matrix{Int64}:
 1  4  7  10
 2  5  8  11
 3  6  9  12

julia> accumulate(+, fill(1, 2, 5), dims=2, init=100.0)
2×5 Matrix{Float64}:
 101.0  102.0  103.0  104.0  105.0
 101.0  102.0  103.0  104.0  105.0
```
