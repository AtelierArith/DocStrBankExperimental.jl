```
maxintfloat(T, S)
```

在给定的浮点类型 `T` 中可表示的最大连续整数，同时不超过整数类型 `S` 可表示的最大整数。等价地，它是 `maxintfloat(T)` 和 [`typemax(S)`](@ref) 的最小值。
