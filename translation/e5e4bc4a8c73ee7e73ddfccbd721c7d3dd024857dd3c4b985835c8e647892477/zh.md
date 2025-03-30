```
versioninfo(io::IO=stdout; verbose::Bool=false)
```

打印有关正在使用的 Julia 版本的信息。输出由布尔关键字参数控制：

  * `verbose`：打印所有附加信息

!!! warning
    此函数的输出可能包含敏感信息。在共享输出之前，请检查输出并删除任何不应公开共享的数据。


另请参见：[`VERSION`](@ref).
