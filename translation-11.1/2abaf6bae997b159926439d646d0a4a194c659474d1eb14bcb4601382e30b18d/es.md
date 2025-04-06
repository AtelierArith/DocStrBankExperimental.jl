```
cis(x)
```

Método más eficiente para `exp(im*x)` utilizando la fórmula de Euler: $\cos(x) + i \sin(x) = \exp(i x)$.

Ver también [`cispi`](@ref), [`sincos`](@ref), [`exp`](@ref), [`angle`](@ref).

# Ejemplos

```jldoctest
julia> cis(π) ≈ -1
true
```
