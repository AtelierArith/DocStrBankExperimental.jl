```
@allocations
```

一个宏，用于评估一个表达式，丢弃结果值，而是返回在评估表达式期间的总分配次数。

另见 [`@allocated`](@ref), [`@time`](@ref), [`@timev`](@ref), [`@timed`](@ref), 和 [`@elapsed`](@ref)。

```julia-repl
julia> @allocations rand(10^6)
2
```

!!! compat "Julia 1.9"
    这个宏是在 Julia 1.9 中添加的。

