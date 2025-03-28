```
first(coll)
```

Obtiene el primer elemento de una colección iterable. Devuelve el punto de inicio de un [`AbstractRange`](@ref) incluso si está vacío.

Véase también: [`only`](@ref), [`firstindex`](@ref), [`last`](@ref).

# Ejemplos

```jldoctest
julia> first(2:2:10)
2

julia> first([1; 2; 3; 4])
1
```
