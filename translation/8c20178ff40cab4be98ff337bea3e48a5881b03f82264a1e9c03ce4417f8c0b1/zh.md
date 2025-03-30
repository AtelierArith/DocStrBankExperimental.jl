```
withenv(f, kv::Pair...)
```

在一个临时修改（而不是像 `setenv` 那样替换）环境中执行 `f`，通过零个或多个 `"var"=>val` 参数 `kv`。`withenv` 通常通过 `withenv(kv...) do ... end` 语法使用。可以使用 `nothing` 的值来临时取消设置环境变量（如果已设置）。当 `withenv` 返回时，原始环境已被恢复。

!!! warning
    更改环境不是线程安全的。对于使用与父进程不同的环境运行外部命令，建议使用 [`addenv`](@ref) 而不是 `withenv`。

