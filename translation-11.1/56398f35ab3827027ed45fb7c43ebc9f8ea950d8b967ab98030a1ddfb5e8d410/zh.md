```
@test_warn msg expr
```

测试评估 `expr` 是否产生包含 `msg` 字符串或与 `msg` 正则表达式匹配的 [`stderr`](@ref) 输出。如果 `msg` 是一个布尔函数，则测试 `msg(output)` 是否返回 `true`。如果 `msg` 是一个元组或数组，则检查错误输出是否包含/匹配 `msg` 中的每个项。返回评估 `expr` 的结果。

另请参见 [`@test_nowarn`](@ref) 以检查错误输出的缺失。

注意：由 `@warn` 生成的警告不能使用此宏进行测试。请改用 [`@test_logs`](@ref)。
