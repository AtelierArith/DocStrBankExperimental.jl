```
@lock_conflicts
```

Bir ifadeyi değerlendirmek, elde edilen değeri atmak ve bunun yerine değerlendirme sırasında kilit çatışmalarının toplam sayısını döndürmek için bir makro. Burada, bir [`ReentrantLock`](@ref) üzerinde bir kilit denemesi, kilit zaten tutulduğundan beklemeye neden oldu.

Ayrıca bkz. [`@time`](@ref), [`@timev`](@ref) ve [`@timed`](@ref).

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
    Bu makro Julia 1.11'de eklendi.

