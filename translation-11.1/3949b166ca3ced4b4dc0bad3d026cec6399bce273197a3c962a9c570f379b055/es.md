```
nextfloat(x::AbstractFloat, n::Integer)
```

El resultado de `n` aplicaciones iterativas de `nextfloat` a `x` si `n >= 0`, o `-n` aplicaciones de [`prevfloat`](@ref) si `n < 0`.
