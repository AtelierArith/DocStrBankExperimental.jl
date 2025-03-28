```
findlast(A)
```

Devuelve el índice o clave del último valor `true` en `A`. Devuelve `nothing` si no hay un valor `true` en `A`.

Los índices o claves son del mismo tipo que los devueltos por [`keys(A)`](@ref) y [`pairs(A)`](@ref).

Véase también: [`findfirst`](@ref), [`findprev`](@ref), [`findall`](@ref).

# Ejemplos

```jldoctest
julia> A = [true, false, true, false]
4-element Vector{Bool}:
 1
 0
 1
 0

julia> findlast(A)
3

julia> A = falses(2,2);

julia> findlast(A) # devuelve nothing, pero no se imprime en el REPL

julia> A = [true false; true false]
2×2 Matrix{Bool}:
 1  0
 1  0

julia> findlast(A)
CartesianIndex(2, 1)
```
