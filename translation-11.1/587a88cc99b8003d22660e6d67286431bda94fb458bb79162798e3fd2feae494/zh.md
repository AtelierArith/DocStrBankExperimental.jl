```
code_native([io=stdout,], f, types; syntax=:intel, debuginfo=:default, binary=false, dump_module=true)
```

打印为运行与给定泛型函数和类型签名匹配的方法生成的本地汇编指令到 `io`。

  * 通过将 `syntax` 设置为 `:intel`（默认）以使用 intel 语法或 `:att` 以使用 AT&T 语法来设置汇编语法。
  * 通过将 `debuginfo` 设置为 `:source`（默认）或 `:none` 来指定代码注释的详细程度。
  * 如果 `binary` 为 `true`，还将打印每条指令的二进制机器代码，并在前面加上缩略地址。
  * 如果 `dump_module` 为 `false`，则不打印元数据，如 rodata 或指令。
  * 如果 `raw` 为 `false`，则省略不重要的指令（如 safepoint 函数序言）。

另请参见: [`@code_native`](@ref), [`code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_llvm`](@ref)。
