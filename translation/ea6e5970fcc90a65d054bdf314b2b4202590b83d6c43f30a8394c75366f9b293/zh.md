```
reenable_sigint(f::Function)
```

在执行函数期间重新启用 Ctrl-C 处理程序。暂时逆转 [`disable_sigint`](@ref) 的效果。
