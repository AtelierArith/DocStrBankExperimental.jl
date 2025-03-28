```
front(x::Tuple)::Tuple
```

Devuelve un `Tuple` que consiste en todos los componentes de `x` excepto el último.

Véase también: [`first`](@ref), [`tail`](@ref Base.tail).

# Ejemplos

```jldoctest
julia> Base.front((1,2,3))
(1, 2)

julia> Base.front(())
ERROR: ArgumentError: No se puede llamar a front en un tuple vacío.
```
