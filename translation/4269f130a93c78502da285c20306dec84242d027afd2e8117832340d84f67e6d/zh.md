```
redirect_stdin(f::Function, stream)
```

在重定向 [`stdin`](@ref) 到 `stream` 的情况下运行函数 `f`。完成后，[`stdin`](@ref) 将恢复到其先前的设置。
