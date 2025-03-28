```
get!(collection, key, default)
```

Devuelve el valor almacenado para la clave dada, o si no hay un mapeo para la clave, almacena `key => default`, y devuelve `default`.

# Ejemplos

```jldoctest
julia> d = Dict("a"=>1, "b"=>2, "c"=>3);

julia> get!(d, "a", 5)
1

julia> get!(d, "d", 4)
4

julia> d
Dict{String, Int64} con 4 entradas:
  "c" => 3
  "b" => 2
  "a" => 1
  "d" => 4
```
