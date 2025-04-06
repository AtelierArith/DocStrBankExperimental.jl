```
all(itr) -> Bool
```

Prueba si todos los elementos de una colección booleana son `true`, devolviendo `false` tan pronto como se encuentra el primer valor `false` en `itr` (circuito corto). Para hacer un circuito corto en `true`, usa [`any`](@ref).

Si la entrada contiene valores [`missing`](@ref), devuelve `missing` si todos los valores no faltantes son `true` (o, de manera equivalente, si la entrada no contiene ningún valor `false`), siguiendo la [lógica de tres valores](https://es.wikipedia.org/wiki/L%C3%B3gica_de_tres_valores).

Véase también: [`all!`](@ref), [`any`](@ref), [`count`](@ref), [`&`](@ref), , [`&&`](@ref), [`allunique`](@ref).

# Ejemplos

```jldoctest
julia> a = [true,false,false,true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> all(a)
false

julia> all((println(i); v) for (i, v) in enumerate(a))
1
2
false

julia> all([missing, false])
false

julia> all([true, missing])
missing
```
