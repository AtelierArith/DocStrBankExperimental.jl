```
all(p, itr) -> Bool
```

Determina si el predicado `p` devuelve `true` para todos los elementos de `itr`, devolviendo `false` tan pronto como se encuentra el primer elemento en `itr` para el cual `p` devuelve `false` (circuito corto). Para hacer un circuito corto en `true`, usa [`any`](@ref).

Si la entrada contiene valores [`missing`](@ref), devuelve `missing` si todos los valores no faltantes son `true` (o, de manera equivalente, si la entrada no contiene ningún valor `false`), siguiendo la [lógica de tres valores](https://en.wikipedia.org/wiki/Three-valued_logic).

# Ejemplos

```jldoctest
julia> all(i->(4<=i<=6), [4,5,6])
true

julia> all(i -> (println(i); i < 3), 1:10)
1
2
3
false

julia> all(i -> i > 0, [1, missing])
missing

julia> all(i -> i > 0, [-1, missing])
false

julia> all(i -> i > 0, [1, 2])
true
```
