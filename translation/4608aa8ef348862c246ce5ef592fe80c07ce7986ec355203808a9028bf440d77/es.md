```
isempty(collection) -> Bool
```

Determina si una colección está vacía (no tiene elementos).

!!! warning
    `isempty(itr)` puede consumir el siguiente elemento de un iterador con estado `itr` a menos que se defina un método apropiado [`Base.isdone(itr)`](@ref). Los iteradores con estado *deberían* implementar `isdone`, pero es posible que desees evitar usar `isempty` al escribir código genérico que deba soportar cualquier tipo de iterador.


# Ejemplos

```jldoctest
julia> isempty([])
true

julia> isempty([1 2 3])
false
```
