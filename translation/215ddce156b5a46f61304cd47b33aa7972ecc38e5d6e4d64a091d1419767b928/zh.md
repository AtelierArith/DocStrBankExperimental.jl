```
通过调整器 API 创建一个 `Time`。起始点将根据提供的 `h, mi, s, ms, us` 参数构建，并将进行调整，直到 `f::Function` 返回 `true`。调整的步长可以通过 `step` 关键字手动提供。`limit` 提供了调整 API 在抛出错误之前所追求的最大迭代次数（如果 `f::Function` 从未满足）。请注意，默认步长将调整以允许给定参数的更高精度；即如果提供了小时、分钟和秒参数，默认步长将是 `Millisecond(1)` 而不是 `Second(1)`。

# 示例

```

jldoctest julia> Time(t -> minute(t) == 30, 20) 20:30:00

julia> Time(t -> minute(t) == 0, 20) 20:00:00

julia> Time(t -> hour(t) == 10, 3; limit = 5) ERROR: ArgumentError: 调整限制已达到：5 次迭代 Stacktrace: [...] ```
