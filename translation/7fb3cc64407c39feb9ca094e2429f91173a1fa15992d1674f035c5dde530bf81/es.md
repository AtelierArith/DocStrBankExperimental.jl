```
findmax(itr) -> (x, index)
```

Devuelve el elemento máximo de la colección `itr` y su índice o clave. Si hay múltiples elementos máximos, se devolverá el primero. Los valores se comparan con `isless`.

Los índices son del mismo tipo que los devueltos por [`keys(itr)`](@ref) y [`pairs(itr)`](@ref).

Véase también: [`findmin`](@ref), [`argmax`](@ref), [`maximum`](@ref).

# Ejemplos

```jldoctest
julia> findmax([8, 0.1, -9, pi])
(8.0, 1)

julia> findmax([1, 7, 7, 6])
(7, 2)

julia> findmax([1, 7, 7, NaN])
(NaN, 4)
```
