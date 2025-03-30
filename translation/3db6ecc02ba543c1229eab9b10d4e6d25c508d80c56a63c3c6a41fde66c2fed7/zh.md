```
DateTime(f::Function, y[, m, d, h, mi, s]; step=Day(1), limit=10000) -> DateTime
```

通过调整器 API 创建一个 `DateTime`。起始点将根据提供的 `y, m, d...` 参数构建，并将进行调整，直到 `f::Function` 返回 `true`。调整的步长可以通过 `step` 关键字手动提供。`limit` 提供了调整 API 在抛出错误之前所追求的最大迭代次数限制（如果 `f::Function` 永远不满足）。

# 示例

```jldoctest
julia> DateTime(dt -> second(dt) == 40, 2010, 10, 20, 10; step = Second(1))
2010-10-20T10:00:40

julia> DateTime(dt -> hour(dt) == 20, 2010, 10, 20, 10; step = Hour(1), limit = 5)
ERROR: ArgumentError: 调整限制已达到：5 次迭代
Stacktrace:
[...]
```
