```
remotecall_fetch(f, id::Integer, args...; kwargs...)
```

Führt `fetch(remotecall(...))` in einer Nachricht aus. Schlüsselwortargumente, falls vorhanden, werden an `f` weitergegeben. Alle Remote-Ausnahmen werden in einer [`RemoteException`](@ref) erfasst und ausgelöst.

Siehe auch [`fetch`](@ref) und [`remotecall`](@ref).

# Beispiele

```julia-repl
$ julia -p 2

julia> remotecall_fetch(sqrt, 2, 4)
2.0

julia> remotecall_fetch(sqrt, 2, -4)
ERROR: Auf Arbeiter 2:
DomainError mit -4.0:
sqrt wurde mit einem negativen reellen Argument aufgerufen, gibt jedoch nur ein komplexes Ergebnis zurück, wenn es mit einem komplexen Argument aufgerufen wird. Versuchen Sie sqrt(Complex(x)).
...
```
