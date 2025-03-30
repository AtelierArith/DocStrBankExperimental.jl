```
include([mapexpr::Function,] path::AbstractString)
```

在包含模块的全局作用域中评估输入源文件的内容。每个模块（除了使用 `baremodule` 定义的模块）都有自己的 `include` 定义，该定义在该模块中评估文件。返回输入文件最后评估的表达式的结果。在包含期间，任务本地的包含路径被设置为包含文件的目录。嵌套调用 `include` 将相对于该路径进行搜索。此函数通常用于交互式加载源代码，或将分成多个源文件的包中的文件组合在一起。参数 `path` 使用 [`normpath`](@ref) 进行规范化，这将解析相对路径标记，例如 `..` 并将 `/` 转换为适当的路径分隔符。

可选的第一个参数 `mapexpr` 可用于在评估之前转换包含的代码：对于 `path` 中的每个解析表达式 `expr`，`include` 函数实际上评估 `mapexpr(expr)`。如果省略，则 `mapexpr` 默认为 [`identity`](@ref)。

使用 [`Base.include`](@ref) 将文件评估到另一个模块中。

!!! compat "Julia 1.5"
    需要 Julia 1.5 才能传递 `mapexpr` 参数。

