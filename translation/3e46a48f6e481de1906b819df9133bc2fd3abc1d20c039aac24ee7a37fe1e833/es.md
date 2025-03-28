```
findall(A)
```

Devuelve un vector `I` de los índices o claves `true` de `A`. Si no hay tales elementos en `A`, devuelve un array vacío. Para buscar otros tipos de valores, pasa un predicado como el primer argumento.

Los índices o claves son del mismo tipo que los devueltos por [`keys(A)`](@ref) y [`pairs(A)`](@ref).

Véase también: [`findfirst`](@ref), [`searchsorted`](@ref).

# Ejemplos

```jldoctest
julia> A = [true, false, false, true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> findall(A)
2-element Vector{Int64}:
 1
 4

julia> A = [true false; false true]
2×2 Matrix{Bool}:
 1  0
 0  1

julia> findall(A)
2-element Vector{CartesianIndex{2}}:
 CartesianIndex(1, 1)
 CartesianIndex(2, 2)

julia> findall(falses(3))
Int64[]
```
