```
map!(función, destino, colección...)
```

Como [`map`](@ref), pero almacena el resultado en `destino` en lugar de en una nueva colección. `destino` debe ser al menos tan grande como la colección más pequeña.

!!! advertencia
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.


Véase también: [`map`](@ref), [`foreach`](@ref), [`zip`](@ref), [`copyto!`](@ref).

# Ejemplos

```jldoctest
julia> a = zeros(3);

julia> map!(x -> x * 2, a, [1, 2, 3]);

julia> a
3-element Vector{Float64}:
 2.0
 4.0
 6.0

julia> map!(+, zeros(Int, 5), 100:999, 1:3)
5-element Vector{Int64}:
 101
 103
 105
   0
   0
```
