```
nextfloat(x::AbstractFloat, n::Integer)
```

Le résultat de `n` applications itératives de `nextfloat` à `x` si `n >= 0`, ou `-n` applications de [`prevfloat`](@ref) si `n < 0`.
