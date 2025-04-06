```
@lock_conflicts
```

一个宏，用于评估一个表达式，丢弃结果值，而是返回评估期间锁冲突的总数，其中对[`ReentrantLock`](@ref)的锁尝试由于锁已被持有而导致等待。

另见[`@time`](@ref)、[`@timev`](@ref)和[`@timed`](@ref)。

```julia-repl
julia> @lock_conflicts begin
    l = ReentrantLock()
    Threads.@threads for i in 1:Threads.nthreads()
        lock(l) do
        sleep(1)
        end
    end
end
5
```

!!! compat "Julia 1.11"
    此宏是在Julia 1.11中添加的。

