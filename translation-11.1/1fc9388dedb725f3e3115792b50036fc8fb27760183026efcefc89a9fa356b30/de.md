```
@spawnat p expr
```

Erstellen Sie einen Closure um einen Ausdruck und führen Sie den Closure asynchron auf dem Prozess `p` aus. Geben Sie ein [`Future`](@ref) zum Ergebnis zurück. Wenn `p` das zitierte literale Symbol `:any` ist, wählt das System automatisch einen Prozessor aus.

# Beispiele

```julia-repl
julia> addprocs(3);

julia> f = @spawnat 2 myid()
Future(2, 1, 3, nothing)

julia> fetch(f)
2

julia> f = @spawnat :any myid()
Future(3, 1, 7, nothing)

julia> fetch(f)
3
```

!!! compat "Julia 1.3"
    Das Argument `:any` ist seit Julia 1.3 verfügbar.

