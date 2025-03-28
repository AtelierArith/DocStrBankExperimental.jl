```
nextfloat(x::AbstractFloat, n::Integer)
```

Das Ergebnis von `n` iterativen Anwendungen von `nextfloat` auf `x`, wenn `n >= 0`, oder `-n` Anwendungen von [`prevfloat`](@ref), wenn `n < 0`.
