```
Experimental.show_error_hints(io, ex, args...)
```

调用来自 [`Experimental.register_error_hint`](@ref) 的所有处理程序，针对特定异常类型 `typeof(ex)`。`args` 必须包含该类型的处理程序所期望的任何其他参数。

!!! compat "Julia 1.5"
    从 Julia 1.5 开始提供自定义错误提示。


!!! warning
    此接口是实验性的，可能会在没有通知的情况下更改或删除。

