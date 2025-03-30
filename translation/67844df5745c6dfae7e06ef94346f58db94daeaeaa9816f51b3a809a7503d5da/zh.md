```
code_llvm([io=stdout,], f, types; raw=false, dump_module=false, optimize=true, debuginfo=:default)
```

打印为运行与给定的泛型函数和类型签名匹配的方法生成的 LLVM 位码到 `io`。

如果未设置 `optimize` 关键字，则代码将在 LLVM 优化之前显示。所有元数据和 dbg.* 调用都将从打印的位码中移除。要获取完整的 IR，请将 `raw` 关键字设置为 true。要转储封装函数的整个模块（包括声明），请将 `dump_module` 关键字设置为 true。关键字参数 `debuginfo` 可以是 source（默认）或 none，以指定代码注释的详细程度。

另请参见: [`@code_llvm`](@ref), [`code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_native`](@ref)。
