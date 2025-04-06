```
llvmcall(fun_ir::String, returntype, Tuple{argtype1, ...}, argvalue1, ...)
llvmcall((mod_ir::String, entry_fn::String), returntype, Tuple{argtype1, ...}, argvalue1, ...)
llvmcall((mod_bc::Vector{UInt8}, entry_fn::String), returntype, Tuple{argtype1, ...}, argvalue1, ...)
```

调用第一个参数中提供的LLVM代码。可以通过几种方式指定此第一个参数：

  * 作为一个字面字符串，表示函数级别的IR（类似于LLVM的`define`块），其中参数作为连续的未命名SSA变量（%0, %1等）可用；
  * 作为一个包含模块IR字符串和表示要调用的入口点函数名称的字符串的2元素元组；
  * 作为一个2元素元组，但模块以`Vector{UInt8}`形式提供，包含位码。

请注意，与`ccall`相反，参数类型必须指定为元组类型，而不是类型的元组。所有类型以及LLVM代码都应作为字面量指定，而不是变量或表达式（可能需要使用`@eval`来生成这些字面量）。

[不透明指针](https://llvm.org/docs/OpaquePointers.html)（写作`ptr`）在LLVM代码中是不允许的。

有关用法示例，请参见[`test/llvmcall.jl`](https://github.com/JuliaLang/julia/blob/v1.11.4/test/llvmcall.jl)。
