```
findmax(f, domain) -> (f(x), index)
```

Devuelve un par de un valor en el codominio (salidas de `f`) y el índice o clave del valor correspondiente en el `domain` (entradas a `f`) tal que `f(x)` está maximizado. Si hay múltiples puntos máximos, se devolverá el primero.

`domain` debe ser un iterable no vacío que soporte [`keys`](@ref). Los índices son del mismo tipo que los devueltos por [`keys(domain)`](@ref).

Los valores se comparan con `isless`.

!!! compat "Julia 1.7"
    Este método requiere Julia 1.7 o posterior.


# Ejemplos

```jldoctest
julia> findmax(identity, 5:9)
(9, 5)

julia> findmax(-, 1:10)
(-1, 1)

julia> findmax(first, [(1, :a), (3, :b), (3, :c)])
(3, 2)

julia> findmax(cos, 0:π/2:2π)
(1.0, 1)
```
