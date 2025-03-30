```
require(into::Module, module::Symbol)
```

此函数是 [`using`](@ref) / [`import`](@ref) 实现的一部分，如果模块尚未在 `Main` 中定义。它也可以直接调用，以强制重新加载模块，无论它之前是否已被加载（例如，在交互式开发库时）。

在每个活动节点的 `Main` 模块上下文中加载源文件，搜索标准位置的文件。`require` 被视为顶级操作，因此它设置当前的 `include` 路径，但不使用它来搜索文件（请参见 [`include`](@ref) 的帮助）。此函数通常用于加载库代码，并由 `using` 隐式调用以加载包。

在搜索文件时，`require` 首先在全局数组 [`LOAD_PATH`](@ref) 中查找包代码。`require` 在所有平台上都是区分大小写的，包括那些具有不区分大小写文件系统的 macOS 和 Windows。

有关代码加载的更多详细信息，请参见手册中关于 [modules](@ref modules) 和 [parallel computing](@ref code-availability) 的部分。
