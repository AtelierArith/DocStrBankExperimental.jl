```
argmax(itr)
```

Devuelve el índice o clave del elemento máximo en una colección. Si hay múltiples elementos máximos, se devolverá el primero.

La colección no debe estar vacía.

Los índices son del mismo tipo que los devueltos por [`keys(itr)`](@ref) y [`pairs(itr)`](@ref).

Los valores se comparan con `isless`.

Véase también: [`argmin`](@ref), [`findmax`](@ref).

# Ejemplos

```jldoctest
julia> argmax([8, 0.1, -9, pi])
1

julia> argmax([1, 7, 7, 6])
2

julia> argmax([1, 7, 7, NaN])
4
```
