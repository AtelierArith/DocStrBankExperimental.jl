```
pop!(collection, key[, default])
```

Elimina y devuelve el mapeo para `key` si existe en `collection`, de lo contrario devuelve `default`, o lanza un error si `default` no está especificado.

# Ejemplos

```jldoctest
julia> d = Dict("a"=>1, "b"=>2, "c"=>3);

julia> pop!(d, "a")
1

julia> pop!(d, "d")
ERROR: KeyError: key "d" not found
Stacktrace:
[...]

julia> pop!(d, "e", 4)
4
```
