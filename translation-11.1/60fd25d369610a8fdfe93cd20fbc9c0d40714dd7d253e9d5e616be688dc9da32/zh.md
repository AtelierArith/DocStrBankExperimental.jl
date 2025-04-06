```
@cfunction(callable, ReturnType, (ArgumentTypes...,)) -> Ptr{Cvoid}
@cfunction($callable, ReturnType, (ArgumentTypes...,)) -> CFunction
```

生成一个 C 可调用的函数指针，从给定类型签名的 Julia 函数 `callable`。要将返回值传递给 `ccall`，请在签名中使用参数类型 `Ptr{Cvoid}`。

请注意，参数类型元组必须是字面量元组，而不是元组值变量或表达式（尽管它可以包含展开表达式）。并且这些参数将在编译时在全局作用域中进行评估（而不是推迟到运行时）。在函数参数前添加 '$' 会将其更改为在局部变量 `callable` 上创建一个运行时闭包（这并不支持所有架构）。

请参阅 [manual section on ccall and cfunction usage](@ref Calling-C-and-Fortran-Code)。

# 示例

```julia-repl
julia> function foo(x::Int, y::Int)
           return x + y
       end

julia> @cfunction(foo, Int, (Int, Int))
Ptr{Cvoid} @0x000000001b82fcd0
```
