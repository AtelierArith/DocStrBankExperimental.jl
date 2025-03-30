```
Base.include([mapexpr::Function,] m::Module, path::AbstractString)
```

在模块 `m` 的全局作用域中评估输入源文件的内容。每个模块（除了使用 [`baremodule`](@ref) 定义的模块）都有自己的 `include` 定义，省略 `m` 参数，这会在该模块中评估文件。返回输入文件最后评估的表达式的结果。在包含期间，任务本地的包含路径被设置为包含文件的目录。嵌套调用 `include` 将相对于该路径进行搜索。此函数通常用于交互式加载源代码，或将分成多个源文件的包中的文件组合在一起。

可选的第一个参数 `mapexpr` 可用于在评估之前转换包含的代码：对于 `path` 中的每个解析表达式 `expr`，`include` 函数实际上评估 `mapexpr(expr)`。如果省略，则 `mapexpr` 默认为 [`identity`](@ref)。

!!! compat "Julia 1.5"
    需要 Julia 1.5 才能传递 `mapexpr` 参数。

