```
@showtime expr
```

类似于 `@time`，但还会打印出被评估的表达式以供参考。

!!! compat "Julia 1.8"
    此宏是在 Julia 1.8 中添加的。


另见 [`@time`](@ref)。

```julia-repl
julia> @showtime sleep(1)
sleep(1): 1.002164 seconds (4 allocations: 128 bytes)
```
