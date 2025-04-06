```
cis(x)
```

Euler formülünü kullanarak `exp(im*x)` için daha verimli bir yöntem: $\cos(x) + i \sin(x) = \exp(i x)$.

Ayrıca bkz. [`cispi`](@ref), [`sincos`](@ref), [`exp`](@ref), [`angle`](@ref).

# Örnekler

```jldoctest
julia> cis(π) ≈ -1
true
```
