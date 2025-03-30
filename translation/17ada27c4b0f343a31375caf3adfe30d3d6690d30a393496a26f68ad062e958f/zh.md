```
@test_nowarn expr
```

测试评估 `expr` 是否产生空的 [`stderr`](@ref) 输出（没有警告或其他消息）。返回评估 `expr` 的结果。

注意：无法使用此宏测试 `@warn` 生成的警告缺失。请改用 [`@test_logs`](@ref)。
