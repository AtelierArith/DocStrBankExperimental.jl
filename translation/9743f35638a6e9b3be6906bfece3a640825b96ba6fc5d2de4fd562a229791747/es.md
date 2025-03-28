```
prevfloat(x::AbstractFloat, n::Integer)
```

El resultado de `n` aplicaciones iterativas de `prevfloat` a `x` si `n >= 0`, o `-n` aplicaciones de [`nextfloat`](@ref) si `n < 0`.
