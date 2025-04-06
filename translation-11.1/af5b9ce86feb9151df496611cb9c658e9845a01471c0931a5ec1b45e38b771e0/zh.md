```
clear!(syms, pids=workers(); mod=Main)
```

通过将全局绑定初始化为 `nothing` 来清除模块中的全局绑定。 `syms` 应该是 [`Symbol`](@ref) 类型或 `Symbol` 的集合。 `pids` 和 `mod` 用于标识要重新初始化全局变量的进程和模块。 只有在 `mod` 下定义的名称才会被清除。

如果请求清除全局常量，将引发异常。
