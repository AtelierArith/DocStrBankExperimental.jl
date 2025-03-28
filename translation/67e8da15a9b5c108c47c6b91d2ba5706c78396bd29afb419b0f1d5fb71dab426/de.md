```
myid()
```

Holen Sie sich die ID des aktuellen Prozesses.

# Beispiele

```julia-repl
julia> myid()
1

julia> remotecall_fetch(() -> myid(), 4)
4
```
