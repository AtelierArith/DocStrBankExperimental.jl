```
@code_native
```

评估函数或宏调用的参数，确定它们的类型，并在结果表达式上调用 [`code_native`](@ref)。

通过在函数调用之前放置可选的关键字参数 `syntax`、`debuginfo`、`binary` 或 `dump_module` 来设置它们，例如：

```
@code_native syntax=:intel debuginfo=:default binary=true dump_module=false f(x)
```

  * 通过将 `syntax` 设置为 `:intel`（默认）来设置汇编语法以使用 Intel 语法，或设置为 `:att` 以使用 AT&T 语法。
  * 通过将 `debuginfo` 设置为 `:source`（默认）或 `:none` 来指定代码注释的详细程度。
  * 如果 `binary` 为 `true`，还会打印每条指令的二进制机器代码，并在前面加上缩略地址。
  * 如果 `dump_module` 为 `false`，则不打印元数据，例如 rodata 或指令。

另请参见：[`code_native`](@ref)、[`@code_warntype`](@ref)、[`@code_typed`](@ref)、[`@code_lowered`](@ref)、[`@code_llvm`](@ref)。
