```
round([T,] x, [r::RoundingMode])
round(x, [r::RoundingMode]; digits::Integer=0, base = 10)
round(x, [r::RoundingMode]; sigdigits::Integer, base = 10)
```

Redondea el número `x`.

Sin argumentos de palabra clave, `x` se redondea a un valor entero, devolviendo un valor del tipo `T`, o del mismo tipo que `x` si no se proporciona `T`. Se lanzará un [`InexactError`](@ref) si el valor no es representable por `T`, similar a [`convert`](@ref).

Si se proporciona el argumento de palabra clave `digits`, se redondea al número especificado de dígitos después del punto decimal (o antes si es negativo), en base `base`.

Si se proporciona el argumento de palabra clave `sigdigits`, se redondea al número especificado de dígitos significativos, en base `base`.

El [`RoundingMode`](@ref) `r` controla la dirección del redondeo; el valor predeterminado es [`RoundNearest`](@ref), que redondea al entero más cercano, con empates (valores fraccionarios de 0.5) redondeados al entero par más cercano. Tenga en cuenta que `round` puede dar resultados incorrectos si se cambia el modo de redondeo global (ver [`rounding`](@ref)).

Al redondear a un tipo de punto flotante, se redondeará a enteros representables por ese tipo (y Inf) en lugar de enteros verdaderos. Inf se trata como un ulp mayor que el `floatmax(T)` a efectos de determinar "más cercano", similar a [`convert`](@ref).

# Ejemplos

```jldoctest
julia> round(1.7)
2.0

julia> round(Int, 1.7)
2

julia> round(1.5)
2.0

julia> round(2.5)
2.0

julia> round(pi; digits=2)
3.14

julia> round(pi; digits=3, base=2)
3.125

julia> round(123.456; sigdigits=2)
120.0

julia> round(357.913; sigdigits=4, base=2)
352.0

julia> round(Float16, typemax(UInt128))
Inf16

julia> floor(Float16, typemax(UInt128))
Float16(6.55e4)
```

!!! nota
    Redondear a dígitos especificados en bases distintas de 2 puede ser inexacto al operar con números de punto flotante binarios. Por ejemplo, el valor [`Float64`](@ref) representado por `1.15` es en realidad *menor* que 1.15, sin embargo, se redondeará a 1.2. Por ejemplo:

    ```jldoctest
    julia> x = 1.15
    1.15

    julia> big(1.15)
    1.149999999999999911182158029987476766109466552734375

    julia> x < 115//100
    true

    julia> round(x, digits=1)
    1.2
    ```


# Extensiones

Para extender `round` a nuevos tipos numéricos, generalmente es suficiente definir `Base.round(x::NewType, r::RoundingMode)`. ```
