```
acquire(f, s::Semaphore)
```

Exécute `f` après avoir acquis le sémaphore `s`, et `release` à la fin ou en cas d'erreur.

Par exemple, une forme de bloc do qui garantit que seulement 2 appels de `foo` seront actifs en même temps :

```julia
s = Base.Semaphore(2)
@sync for _ in 1:100
    Threads.@spawn begin
        Base.acquire(s) do
            foo()
        end
    end
end
```

!!! compat "Julia 1.8"
    Cette méthode nécessite au moins Julia 1.8.

