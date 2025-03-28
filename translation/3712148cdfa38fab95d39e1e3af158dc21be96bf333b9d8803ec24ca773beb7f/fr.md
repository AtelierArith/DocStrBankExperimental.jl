```
procs()
```

Renvoie une liste de tous les identifiants de processus, y compris le pid 1 (qui n'est pas inclus par [`workers()`](@ref)).

# Exemples

```julia-repl
$ julia -p 2

julia> procs()
3-element Array{Int64,1}:
 1
 2
 3
```
