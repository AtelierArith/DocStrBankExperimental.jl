```
StepRange{T, S} <: OrdinalRange{T, S}
```

Rangos con elementos de tipo `T` con espaciado de tipo `S`. El paso entre cada elemento es constante, y el rango se define en términos de un `start` y `stop` de tipo `T` y un `step` de tipo `S`. Ni `T` ni `S` deben ser tipos de punto flotante. La sintaxis `a:b:c` con `b != 0` y `a`, `b`, y `c` todos enteros crea un `StepRange`.

# Ejemplos

```jldoctest
julia> collect(StepRange(1, Int8(2), 10))
5-element Vector{Int64}:
 1
 3
 5
 7
 9

julia> typeof(StepRange(1, Int8(2), 10))
StepRange{Int64, Int8}

julia> typeof(1:3:6)
StepRange{Int64, Int64}
```
