```
try/catch
```

`try`/`catch` 语句允许拦截由 [`throw`](@ref) 抛出的错误（异常），以便程序执行可以继续。例如，以下代码尝试写入一个文件，但如果文件无法写入，则警告用户并继续执行，而不是终止执行：

```julia
try
    open("/danger", "w") do f
        println(f, "Hello")
    end
catch
    @warn "Could not write file."
end
```

或者，当文件无法读取到变量中时：

```julia
lines = try
    open("/danger", "r") do f
        readlines(f)
    end
catch
    @warn "File not found."
end
```

语法 `catch e`（其中 `e` 是任何变量）将抛出的异常对象分配给 `catch` 块中的给定变量。

`try`/`catch` 结构的强大之处在于能够立即将深度嵌套的计算展开到调用函数栈中的更高层次。
