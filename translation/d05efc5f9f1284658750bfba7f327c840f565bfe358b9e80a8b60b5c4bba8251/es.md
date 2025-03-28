```
argmin(itr)
```

Devuelve el índice o clave del elemento mínimo en una colección. Si hay múltiples elementos mínimos, se devolverá el primero.

La colección no debe estar vacía.

Los índices son del mismo tipo que los devueltos por [`keys(itr)`](@ref) y [`pairs(itr)`](@ref).

`NaN` se trata como menor que todos los demás valores excepto `missing`.

Véase también: [`argmax`](@ref), [`findmin`](@ref).

# Ejemplos

```jldoctest
julia> argmin([8, 0.1, -9, pi])
3

julia> argmin([7, 1, 1, 6])
2

julia> argmin([7, 1, 1, NaN])
4
```
