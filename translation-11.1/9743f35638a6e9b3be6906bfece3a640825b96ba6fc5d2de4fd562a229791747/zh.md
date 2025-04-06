```
prevfloat(x::AbstractFloat, n::Integer)
```

如果 `n >= 0`，则对 `x` 进行 `n` 次迭代应用 `prevfloat` 的结果；如果 `n < 0`，则进行 `-n` 次 [`nextfloat`](@ref) 的应用。
