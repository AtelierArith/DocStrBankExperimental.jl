```
acquire(f, s::Semaphore)
```

Führen Sie `f` aus, nachdem Sie von Semaphore `s` erworben haben, und `release` nach Abschluss oder Fehler.

Zum Beispiel eine do-Block-Form, die sicherstellt, dass nur 2 Aufrufe von `foo` gleichzeitig aktiv sind:

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
    Diese Methode erfordert mindestens Julia 1.8.

