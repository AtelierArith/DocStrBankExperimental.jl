```
code_warntype([io::IO], f, types; debuginfo=:default)
```

打印与给定的泛型函数和类型签名匹配的方法的降低和类型推断的 AST，`io` 默认为 `stdout`。AST 被注释为强调可能对性能有问题的“非叶”类型（如果可用颜色，则以红色显示）。这作为潜在类型不稳定的警告。

并非所有非叶类型对性能都特别有问题，特定类型的性能特征是编译器的实现细节。`code_warntype` 会倾向于将可能影响性能的类型标记为红色，因此某些类型即使不影响性能也可能被标记为红色。小的具体类型联合通常不是问题，因此这些会以黄色突出显示。

关键字参数 `debuginfo` 可以是 `:source` 或 `:none`（默认），用于指定代码注释的详细程度。

有关更多信息，请参见手册中性能提示页面的 [`@code_warntype`](@ref man-code-warntype) 部分。

另请参见：[`@code_warntype`](@ref)，[`code_typed`](@ref)，[`code_lowered`](@ref)，[`code_llvm`](@ref)，[`code_native`](@ref)。
