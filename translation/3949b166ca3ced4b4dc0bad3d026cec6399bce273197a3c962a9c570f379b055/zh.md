```
nextfloat(x::AbstractFloat, n::Integer)
```

如果 `n >= 0`，则返回对 `x` 进行 `n` 次迭代应用 `nextfloat` 的结果；如果 `n < 0`，则返回对 [`prevfloat`](@ref) 进行 `-n` 次应用的结果。
