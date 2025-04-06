```
any(itr) -> Bool
```

Prueba si algún elemento de una colección booleana es `true`, devolviendo `true` tan pronto como se encuentra el primer valor `true` en `itr` (circuito corto). Para hacer un circuito corto en `false`, usa [`all`](@ref).

Si la entrada contiene valores [`missing`](@ref), devuelve `missing` si todos los valores no faltantes son `false` (o, de manera equivalente, si la entrada no contiene ningún valor `true`), siguiendo la [lógica de tres valores](https://en.wikipedia.org/wiki/Three-valued_logic).

Véase también: [`all`](@ref), [`count`](@ref), [`sum`](@ref), [`|`](@ref), , [`||`](@ref).

# Ejemplos

```jldoctest
julia> a = [true,false,false,true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> any(a)
true

julia> any((println(i); v) for (i, v) in enumerate(a))
1
true

julia> any([missing, true])
true

julia> any([false, missing])
missing
```
