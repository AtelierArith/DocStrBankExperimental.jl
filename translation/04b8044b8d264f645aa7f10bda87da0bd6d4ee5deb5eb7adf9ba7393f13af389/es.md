```
values(a::AbstractDict)
```

Devuelve un iterador sobre todos los valores en una colección. `collect(values(a))` devuelve un array de valores. Cuando los valores se almacenan internamente en una tabla hash, como es el caso de `Dict`, el orden en que se devuelven puede variar. Pero `keys(a)`, `values(a)` y `pairs(a)` iteran sobre `a` y devuelven los elementos en el mismo orden.

# Ejemplos

```jldoctest
julia> D = Dict('a'=>2, 'b'=>3)
Dict{Char, Int64} con 2 entradas:
  'a' => 2
  'b' => 3

julia> collect(values(D))
Vector{Int64} de 2 elementos:
 2
 3
```
