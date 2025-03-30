```
@lock l expr
```

`lock(f, l::AbstractLock)` 的宏版本，但使用 `expr` 而不是 `f` 函数。展开为：

```julia
lock(l)
try
    expr
finally
    unlock(l)
end
```

这类似于使用 [`lock`](@ref) 和 `do` 块，但避免了创建闭包，从而可以提高性能。

!!! compat
    `@lock` 在 Julia 1.3 中添加，并在 Julia 1.10 中导出。

