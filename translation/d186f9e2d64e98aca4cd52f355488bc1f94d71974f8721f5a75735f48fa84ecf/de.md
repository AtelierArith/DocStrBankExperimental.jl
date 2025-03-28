```
@lock_conflicts
```

Ein Makro zur Auswertung eines Ausdrucks, das den resultierenden Wert verwirft und stattdessen die Gesamtzahl der Lock-Konflikte während der Auswertung zurückgibt, wobei ein Lock-Versuch auf einem [`ReentrantLock`](@ref) zu einem Warten führte, weil der Lock bereits gehalten wurde.

Siehe auch [`@time`](@ref), [`@timev`](@ref) und [`@timed`](@ref).

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
    Dieses Makro wurde in Julia 1.11 hinzugefügt.

