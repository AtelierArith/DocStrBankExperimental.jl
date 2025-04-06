```
cis(A::AbstractMatrix)
```

Método más eficiente para `exp(im*A)` de la matriz cuadrada `A` (especialmente si `A` es `Hermitiana` o `Simétrica` real).

Véase también [`cispi`](@ref), [`sincos`](@ref), [`exp`](@ref).

!!! compat "Julia 1.7"
    El soporte para usar `cis` con matrices se agregó en Julia 1.7.


# Ejemplos

```jldoctest
julia> cis([π 0; 0 π]) ≈ -I
true
```
