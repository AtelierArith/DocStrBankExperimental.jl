```
redirect_stdout(f::Function, stream)
```

在重定向 [`stdout`](@ref) 到 `stream` 的情况下运行函数 `f`。完成后，[`stdout`](@ref) 将恢复到之前的设置。
