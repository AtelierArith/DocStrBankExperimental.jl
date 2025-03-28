```
vect(X...)
```

Crea un [`Vector`](@ref) con el tipo de elemento calculado a partir del `promote_typeof` del argumento, que contiene la lista de argumentos.

# Ejemplos

```jldoctest
julia> a = Base.vect(UInt8(1), 2.5, 1//2)
3-element Vector{Float64}:
 1.0
 2.5
 0.5
```
