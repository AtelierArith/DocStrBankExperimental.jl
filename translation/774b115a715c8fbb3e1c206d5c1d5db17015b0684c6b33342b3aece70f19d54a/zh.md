```
@code_llvm
```

评估函数或宏调用的参数，确定它们的类型，并在结果表达式上调用 [`code_llvm`](@ref)。通过将可选关键字参数 `raw`、`dump_module`、`debuginfo`、`optimize` 及其值放在函数调用之前来设置它们，如下所示：

```
@code_llvm raw=true dump_module=true debuginfo=:default f(x)
@code_llvm optimize=false f(x)
```

`optimize` 控制是否应用额外的优化，例如内联。`raw` 使所有元数据和 dbg.* 调用可见。`debuginfo` 可以是 `:source`（默认）或 `:none`，以指定代码注释的详细程度。`dump_module` 打印封装该函数的整个模块。

另请参见：[`code_llvm`](@ref)，[`@code_warntype`](@ref)，[`@code_typed`](@ref)，[`@code_lowered`](@ref)，[`@code_native`](@ref)。
