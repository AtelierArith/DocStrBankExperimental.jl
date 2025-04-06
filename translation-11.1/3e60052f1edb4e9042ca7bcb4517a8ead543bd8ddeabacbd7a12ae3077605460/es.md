```
filter!(f, a)
```

Actualiza la colección `a`, eliminando elementos para los cuales `f` es `false`. La función `f` recibe un argumento.

# Ejemplos

```jldoctest
julia> filter!(isodd, Vector(1:10))
5-element Vector{Int64}:
 1
 3
 5
 7
 9
```
