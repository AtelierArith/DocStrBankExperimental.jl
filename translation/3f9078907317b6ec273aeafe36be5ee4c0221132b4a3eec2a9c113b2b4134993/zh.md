```
@allocated
```

一个宏，用于评估一个表达式，丢弃结果值，而是返回在评估该表达式期间分配的总字节数。

另见 [`@allocations`](@ref)，[`@time`](@ref)，[`@timev`](@ref)，[`@timed`](@ref) 和 [`@elapsed`](@ref)。

```julia-repl
julia> @allocated rand(10^6)
8000080
```
