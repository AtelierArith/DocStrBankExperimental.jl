```
prevfloat(x::AbstractFloat, n::Integer)
```

Das Ergebnis von `n` iterativen Anwendungen von `prevfloat` auf `x`, wenn `n >= 0`, oder `-n` Anwendungen von [`nextfloat`](@ref), wenn `n < 0`.
