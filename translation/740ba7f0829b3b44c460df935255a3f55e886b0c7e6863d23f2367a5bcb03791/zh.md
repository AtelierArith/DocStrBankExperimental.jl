```
@elapsed
```

一个宏，用于评估一个表达式，丢弃结果值，而是返回执行所需的秒数，作为浮点数。

在某些情况下，系统会查看 `@elapsed` 表达式内部，并在顶层表达式执行开始之前编译一些被调用的代码。当发生这种情况时，一些编译时间将不会被计算在内。要包括这段时间，可以运行 `@elapsed @eval ...`。

另请参见 [`@time`](@ref)、[`@timev`](@ref)、[`@timed`](@ref)、[`@allocated`](@ref) 和 [`@allocations`](@ref)。

```julia-repl
julia> @elapsed sleep(0.3)
0.301391426
```
