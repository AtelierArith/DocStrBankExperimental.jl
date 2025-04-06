```
floatmin(T = Float64)
```

Devuelve el número normal positivo más pequeño que se puede representar con el tipo de punto flotante `T`.

# Ejemplos

```jldoctest
julia> floatmin(Float16)
Float16(6.104e-5)

julia> floatmin(Float32)
1.1754944f-38

julia> floatmin()
2.2250738585072014e-308
```
