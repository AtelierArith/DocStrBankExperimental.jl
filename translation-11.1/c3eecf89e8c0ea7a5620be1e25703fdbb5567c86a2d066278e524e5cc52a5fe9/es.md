```
any(p, itr) -> Bool
```

Determina si el predicado `p` devuelve `true` para algún elemento de `itr`, devolviendo `true` tan pronto como se encuentra el primer elemento en `itr` para el cual `p` devuelve `true` (circuito corto). Para hacer un circuito corto en `false`, usa [`all`](@ref).

Si la entrada contiene valores de [`missing`](@ref), devuelve `missing` si todos los valores no faltantes son `false` (o, de manera equivalente, si la entrada no contiene ningún valor `true`), siguiendo la [lógica de tres valores](https://en.wikipedia.org/wiki/Three-valued_logic).

# Ejemplos

```jldoctest
julia> any(i->(4<=i<=6), [3,5,7])
true

julia> any(i -> (println(i); i > 3), 1:10)
1
2
3
4
true

julia> any(i -> i > 0, [1, missing])
true

julia> any(i -> i > 0, [-1, missing])
missing

julia> any(i -> i > 0, [-1, 0])
false
```
