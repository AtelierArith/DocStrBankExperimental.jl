```
@timed
```

一个宏，用于执行一个表达式，并返回该表达式的值、经过的时间（以秒为单位）、总分配的字节数、垃圾回收时间、一个包含各种内存分配计数器的对象、编译时间（以秒为单位）和重新编译时间（以秒为单位）。任何需要等待的 [`ReentrantLock`](@ref) 的锁冲突将以计数的形式显示。

在某些情况下，系统会查看 `@timed` 表达式内部，并在顶层表达式执行开始之前编译一些被调用的代码。当发生这种情况时，一些编译时间将不会被计算。要包括这段时间，您可以运行 `@timed @eval ...`。

另请参见 [`@time`](@ref)、[`@timev`](@ref)、[`@elapsed`](@ref)、[`@allocated`](@ref)、[`@allocations`](@ref) 和 [`@lock_conflicts`](@ref)。

```julia-repl
julia> stats = @timed rand(10^6);

julia> stats.time
0.006634834

julia> stats.bytes
8000256

julia> stats.gctime
0.0055765

julia> propertynames(stats.gcstats)
(:allocd, :malloc, :realloc, :poolalloc, :bigalloc, :freecall, :total_time, :pause, :full_sweep)

julia> stats.gcstats.total_time
5576500

julia> stats.compile_time
0.0

julia> stats.recompile_time
0.0

```

!!! compat "Julia 1.5"
    此宏的返回类型在 Julia 1.5 中从 `Tuple` 更改为 `NamedTuple`。


!!! compat "Julia 1.11"
    `lock_conflicts`、`compile_time` 和 `recompile_time` 字段在 Julia 1.11 中添加。

