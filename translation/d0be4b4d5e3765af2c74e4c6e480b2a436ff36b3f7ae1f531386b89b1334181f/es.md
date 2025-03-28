```
//(num, den)
```

Divide dos enteros o números racionales, dando un resultado de [`Rational`](@ref). Más generalmente, `//` se puede usar para la división racional exacta de otros tipos numéricos con componentes enteros o racionales, como números complejos con componentes enteros.

Tenga en cuenta que los argumentos de punto flotante ([`AbstractFloat`](@ref)) no están permitidos por `//` (incluso si los valores son racionales). Los argumentos deben ser subtipos de [`Integer`](@ref), `Rational`, o compuestos de estos.

# Ejemplos

```jldoctest
julia> 3 // 5
3//5

julia> (3 // 5) // (2 // 1)
3//10

julia> (1+2im) // (3+4im)
11//25 + 2//25*im

julia> 1.0 // 2
ERROR: MethodError: no method matching //(::Float64, ::Int64)
[...]
```
