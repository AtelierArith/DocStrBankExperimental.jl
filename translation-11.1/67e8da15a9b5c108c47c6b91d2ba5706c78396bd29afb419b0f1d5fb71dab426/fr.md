```
myid()
```

Obtenez l'identifiant du processus actuel.

# Exemples

```julia-repl
julia> myid()
1

julia> remotecall_fetch(() -> myid(), 4)
4
```
