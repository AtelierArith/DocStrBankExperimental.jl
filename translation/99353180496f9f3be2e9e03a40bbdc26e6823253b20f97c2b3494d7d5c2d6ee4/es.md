```
tail(x::Tuple)::Tuple
```

Devuelve un `Tuple` que consiste en todos menos el primer componente de `x`.

Véase también: [`front`](@ref Base.front), [`rest`](@ref Base.rest), [`first`](@ref), [`Iterators.peel`](@ref).

# Ejemplos

```jldoctest
julia> Base.tail((1,2,3))
(2, 3)

julia> Base.tail(())
ERROR: ArgumentError: No se puede llamar a tail en una tupla vacía.
```
