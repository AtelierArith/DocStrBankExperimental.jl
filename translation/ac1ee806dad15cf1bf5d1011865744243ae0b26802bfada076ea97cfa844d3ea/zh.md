```
include_string([mapexpr::Function,] m::Module, code::AbstractString, filename::AbstractString="string")
```

与 [`include`](@ref) 类似，但从给定的字符串中读取代码，而不是从文件中读取。

可选的第一个参数 `mapexpr` 可用于在评估之前转换包含的代码：对于 `code` 中的每个解析表达式 `expr`，`include_string` 函数实际上会评估 `mapexpr(expr)`。如果省略，则 `mapexpr` 默认为 [`identity`](@ref)。

!!! compat "Julia 1.5"
    需要 Julia 1.5 才能传递 `mapexpr` 参数。

