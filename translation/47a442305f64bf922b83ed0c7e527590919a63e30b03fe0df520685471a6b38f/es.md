```
end
```

`end` marca la conclusión de un bloque de expresiones, por ejemplo [`module`](@ref), [`struct`](@ref), [`mutable struct`](@ref), [`begin`](@ref), [`let`](@ref), [`for`](@ref) etc.

`end` también puede ser utilizado al indexar para representar el último índice de una colección o el último índice de una dimensión de un arreglo.

# Ejemplos

```jldoctest
julia> A = [1 2; 3 4]
2×2 Array{Int64, 2}:
 1  2
 3  4

julia> A[end, :]
2-element Array{Int64, 1}:
 3
 4
```
