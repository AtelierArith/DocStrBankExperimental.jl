```
procs()
```

Gibt eine Liste aller Prozess-Identifikatoren zurück, einschließlich pid 1 (die nicht von [`workers()`](@ref) eingeschlossen ist).

# Beispiele

```julia-repl
$ julia -p 2

julia> procs()
3-element Array{Int64,1}:
 1
 2
 3
```
