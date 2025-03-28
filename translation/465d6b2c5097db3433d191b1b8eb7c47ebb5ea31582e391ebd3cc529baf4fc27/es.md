```
trunc([T,] x)
trunc(x; digits::Integer= [, base = 10])
trunc(x; sigdigits::Integer= [, base = 10])
```

`trunc(x)` devuelve el valor integral más cercano del mismo tipo que `x` cuyo valor absoluto es menor o igual al valor absoluto de `x`.

`trunc(T, x)` convierte el resultado al tipo `T`, lanzando un `InexactError` si el valor truncado no es representable como `T`.

Las palabras clave `digits`, `sigdigits` y `base` funcionan como para [`round`](@ref).

Para soportar `trunc` para un nuevo tipo, define `Base.round(x::NewType, ::RoundingMode{:ToZero})`.

Véase también: [`%`](@ref rem), [`floor`](@ref), [`unsigned`](@ref), [`unsafe_trunc`](@ref).

# Ejemplos

```jldoctest
julia> trunc(2.22)
2.0

julia> trunc(-2.22, digits=1)
-2.2

julia> trunc(Int, -2.22)
-2
```
