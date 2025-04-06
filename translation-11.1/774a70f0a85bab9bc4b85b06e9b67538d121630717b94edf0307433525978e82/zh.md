```
@code_typed
```

评估函数或宏调用的参数，确定它们的类型，并在结果表达式上调用 [`code_typed`](@ref)。使用可选参数 `optimize` 进行控制

```
@code_typed optimize=true foo(x)
```

是否应用额外的优化，例如内联。

另请参见：[`code_typed`](@ref)，[`@code_warntype`](@ref)，[`@code_lowered`](@ref)，[`@code_llvm`](@ref)，[`@code_native`](@ref)。
