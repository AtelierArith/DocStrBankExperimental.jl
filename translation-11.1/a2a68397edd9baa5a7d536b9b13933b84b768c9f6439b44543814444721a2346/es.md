```
getkey(collection, key, default)
```

Devuelve la clave que coincide con el argumento `key` si existe en `collection`, de lo contrario devuelve `default`.

# Ejemplos

```jldoctest
julia> D = Dict('a'=>2, 'b'=>3)
Dict{Char, Int64} con 2 entradas:
  'a' => 2
  'b' => 3

julia> getkey(D, 'a', 1)
'a': ASCII/Unicode U+0061 (categoría Ll: Letra, minúscula)

julia> getkey(D, 'd', 'a')
'a': ASCII/Unicode U+0061 (categoría Ll: Letra, minúscula)
```
