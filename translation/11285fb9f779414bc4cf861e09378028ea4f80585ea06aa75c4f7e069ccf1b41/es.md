```
isone(x)
```

Devuelve `true` si `x == one(x)`; si `x` es un arreglo, esto verifica si `x` es una matriz identidad.

# Ejemplos

```jldoctest
julia> isone(1.0)
true

julia> isone([1 0; 0 2])
false

julia> isone([1 0; 0 true])
true
```
