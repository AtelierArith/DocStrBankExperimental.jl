```
get(collection, key, default)
```

Devuelve el valor almacenado para la clave dada, o el valor predeterminado dado si no hay un mapeo para la clave presente.

!!! compat "Julia 1.7"
    Para tuplas y números, esta función requiere al menos Julia 1.7.


# Ejemplos

```jldoctest
julia> d = Dict("a"=>1, "b"=>2);

julia> get(d, "a", 3)
1

julia> get(d, "c", 3)
3
```
