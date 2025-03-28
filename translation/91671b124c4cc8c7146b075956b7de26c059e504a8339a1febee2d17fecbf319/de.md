```
@spawn expr
```

Erstellt einen Closure um einen Ausdruck und führt ihn auf einem automatisch gewählten Prozess aus, wobei ein [`Future`](@ref) zum Ergebnis zurückgegeben wird. Dieses Makro ist veraltet; `@spawnat :any expr` sollte stattdessen verwendet werden.

# Beispiele

```julia-repl
julia> addprocs(3);

julia> f = @spawn myid()
Future(2, 1, 5, nichts)

julia> fetch(f)
2

julia> f = @spawn myid()
Future(3, 1, 7, nichts)

julia> fetch(f)
3
```

!!! compat "Julia 1.3"
    Ab Julia 1.3 ist dieses Makro veraltet. Verwenden Sie stattdessen `@spawnat :any`.

