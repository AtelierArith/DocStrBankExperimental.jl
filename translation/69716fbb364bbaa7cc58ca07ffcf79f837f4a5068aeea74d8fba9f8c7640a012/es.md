```
abs2(x)
```

Valor absoluto al cuadrado de `x`.

Esto puede ser más rápido que `abs(x)^2`, especialmente para números complejos donde `abs(x)` requiere una raíz cuadrada a través de [`hypot`](@ref).

Véase también [`abs`](@ref), [`conj`](@ref), [`real`](@ref).

# Ejemplos

```jldoctest
julia> abs2(-3)
9

julia> abs2(3.0 + 4.0im)
25.0

julia> sum(abs2, [1+2im, 3+4im])  # LinearAlgebra.norm(x)^2
30
```
