```
delete!(collection, key)
```

Elimina la asignación para la clave dada en una colección, si existe, y devuelve la colección.

# Ejemplos

```jldoctest
julia> d = Dict("a"=>1, "b"=>2)
Dict{String, Int64} con 2 entradas:
  "b" => 2
  "a" => 1

julia> delete!(d, "b")
Dict{String, Int64} con 1 entrada:
  "a" => 1

julia> delete!(d, "b") # d permanece sin cambios
Dict{String, Int64} con 1 entrada:
  "a" => 1
```
