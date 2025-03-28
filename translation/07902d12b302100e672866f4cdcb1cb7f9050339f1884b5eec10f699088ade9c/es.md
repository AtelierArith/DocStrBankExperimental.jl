```
findmin(itr) -> (x, index)
```

Devuelve el elemento mínimo de la colección `itr` y su índice o clave. Si hay múltiples elementos mínimos, se devolverá el primero. `NaN` se trata como menor que todos los demás valores excepto `missing`.

Los índices son del mismo tipo que los devueltos por [`keys(itr)`](@ref) y [`pairs(itr)`](@ref).

Véase también: [`findmax`](@ref), [`argmin`](@ref), [`minimum`](@ref).

# Ejemplos

```jldoctest
julia> findmin([8, 0.1, -9, pi])
(-9.0, 3)

julia> findmin([1, 7, 7, 6])
(1, 1)

julia> findmin([1, 7, 7, NaN])
(NaN, 4)
```
