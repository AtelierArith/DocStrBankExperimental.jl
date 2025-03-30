```
ccall((function_name, library), returntype, (argtype1, ...), argvalue1, ...)
ccall(function_name, returntype, (argtype1, ...), argvalue1, ...)
ccall(function_pointer, returntype, (argtype1, ...), argvalue1, ...)
```

调用在 C 导出共享库中的函数，由元组 `(function_name, library)` 指定，其中每个组件可以是字符串或符号。除了指定库外，还可以使用 `function_name` 符号或字符串，这将在当前进程中解析。或者，`ccall` 也可以用于调用函数指针 `function_pointer`，例如由 `dlsym` 返回的指针。

请注意，参数类型元组必须是字面量元组，而不是元组值变量或表达式。

每个传递给 `ccall` 的 `argvalue` 将通过自动插入调用 `unsafe_convert(argtype, cconvert(argtype, argvalue))` 转换为相应的 `argtype`。（有关详细信息，请参见 [`unsafe_convert`](@ref Base.unsafe_convert) 和 [`cconvert`](@ref Base.cconvert) 的文档。）在大多数情况下，这仅会导致对 `convert(argtype, argvalue)` 的调用。
