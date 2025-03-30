```
StackFrame
```

堆栈信息表示执行上下文，具有以下字段：

  * `func::Symbol`

    包含执行上下文的函数名称。
  * `linfo::Union{Core.MethodInstance, Method, Module, Core.CodeInfo, Nothing}`

    包含执行上下文的MethodInstance或CodeInfo（如果可以找到），或Module（用于宏扩展）。
  * `file::Symbol`

    包含执行上下文的文件路径。
  * `line::Int`

    包含执行上下文的文件中的行号。
  * `from_c::Bool`

    如果代码来自C，则为真。
  * `inlined::Bool`

    如果代码来自内联帧，则为真。
  * `pointer::UInt64`

    作为`backtrace`返回的执行上下文指针的表示。
