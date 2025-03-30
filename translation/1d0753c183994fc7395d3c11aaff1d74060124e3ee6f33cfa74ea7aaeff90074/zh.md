```
Date(f::Function, y[, m, d]; step=Day(1), limit=10000) -> Date
```

通过调整器 API 创建一个 `Date`。起始点将根据提供的 `y, m, d` 参数构建，并将进行调整，直到 `f::Function` 返回 `true`。调整的步长可以通过 `step` 关键字手动提供。`limit` 提供了调整 API 在抛出错误之前将追求的最大迭代次数限制（假设 `f::Function` 永远不会满足）。

# 示例

```jldoctest
julia> Date(date -> week(date) == 20, 2010, 01, 01)
2010-05-17

julia> Date(date -> year(date) == 2010, 2000, 01, 01)
2010-01-01

julia> Date(date -> month(date) == 10, 2000, 01, 01; limit = 5)
ERROR: ArgumentError: Adjustment limit reached: 5 iterations
Stacktrace:
[...]
```
