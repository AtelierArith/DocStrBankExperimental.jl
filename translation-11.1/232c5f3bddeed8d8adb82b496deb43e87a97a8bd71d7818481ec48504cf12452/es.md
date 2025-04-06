```
abs(x)
```

El valor absoluto de `x`.

Cuando `abs` se aplica a enteros con signo, puede ocurrir un desbordamiento, lo que resulta en el retorno de un valor negativo. Este desbordamiento ocurre solo cuando `abs` se aplica al valor mínimo representable de un entero con signo. Es decir, cuando `x == typemin(typeof(x))`, `abs(x) == x < 0`, no `-x` como podría esperarse.

Véase también: [`abs2`](@ref), [`unsigned`](@ref), [`sign`](@ref).

# Ejemplos

```jldoctest
julia> abs(-3)
3

julia> abs(1 + im)
1.4142135623730951

julia> abs.(Int8[-128 -127 -126 0 126 127])  # desbordamiento en typemin(Int8)
1×6 Matrix{Int8}:
 -128  127  126  0  126  127

julia> maximum(abs, [1, -2, 3, -4])
4
```
