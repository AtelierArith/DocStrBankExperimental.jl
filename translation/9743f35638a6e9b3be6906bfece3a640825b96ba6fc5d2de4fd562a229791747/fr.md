```
prevfloat(x::AbstractFloat, n::Integer)
```

Le résultat de `n` applications itératives de `prevfloat` à `x` si `n >= 0`, ou `-n` applications de [`nextfloat`](@ref) si `n < 0`.
