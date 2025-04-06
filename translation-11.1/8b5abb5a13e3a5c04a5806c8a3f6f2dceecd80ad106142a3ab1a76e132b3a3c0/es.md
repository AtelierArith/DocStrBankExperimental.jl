```
collect(tipo_de_elemento, colección)
```

Devuelve un `Array` con el tipo de elemento dado de todos los elementos en una colección o iterable. El resultado tiene la misma forma y número de dimensiones que `colección`.

# Ejemplos

```jldoctest
julia> collect(Float64, 1:2:5)
3-element Vector{Float64}:
 1.0
 3.0
 5.0
```
