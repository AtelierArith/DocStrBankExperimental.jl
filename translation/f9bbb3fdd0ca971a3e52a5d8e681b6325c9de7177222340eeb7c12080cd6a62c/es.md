```
findmin(f, domain) -> (f(x), index)
```

Devuelve un par de un valor en el codominio (salidas de `f`) y el índice o clave del valor correspondiente en el `domain` (entradas a `f`) tal que `f(x)` se minimiza. Si hay múltiples puntos mínimos, se devolverá el primero.

`domain` debe ser un iterable no vacío.

Los índices son del mismo tipo que los devueltos por [`keys(domain)`](@ref) y [`pairs(domain)`](@ref).

`NaN` se trata como menor que todos los demás valores excepto `missing`.

!!! compat "Julia 1.7"
    Este método requiere Julia 1.7 o posterior.


# Ejemplos

```jldoctest
julia> findmin(identity, 5:9)
(5, 1)

julia> findmin(-, 1:10)
(-10, 10)

julia> findmin(first, [(2, :a), (2, :b), (3, :c)])
(2, 1)

julia> findmin(cos, 0:π/2:2π)
(-1.0, 3)
```
