```
issubnormal(f) -> Bool
```

Prueba si un número de punto flotante es subnormal.

Un número de punto flotante IEEE es [subnormal](https://en.wikipedia.org/wiki/Subnormal_number) cuando sus bits de exponente son cero y su significante no es cero.

# Ejemplos

```jldoctest
julia> floatmin(Float32)
1.1754944f-38

julia> issubnormal(1.0f-37)
false

julia> issubnormal(1.0f-38)
true
```
