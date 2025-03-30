```
tonext(func::Function, dt::TimeType; step=Day(1), limit=10000, same=false) -> TimeType
```

通过最多迭代 `limit` 次，按 `step` 增量调整 `dt`，直到 `func` 返回 `true`。`func` 必须接受一个 `TimeType` 参数并返回一个 [`Bool`](@ref)。`same` 允许在满足 `func` 时考虑 `dt`。
