```
redirect_stderr(f::Function, stream)
```

在重定向 [`stderr`](@ref) 到 `stream` 的情况下运行函数 `f`。完成后，[`stderr`](@ref) 将恢复到之前的设置。
