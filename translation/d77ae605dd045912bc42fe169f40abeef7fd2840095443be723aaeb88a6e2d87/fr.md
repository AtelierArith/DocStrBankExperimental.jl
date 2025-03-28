```
Threads.threadid() -> Int
```

Obtenez le numéro d'identification du thread d'exécution actuel. Le thread maître a l'ID `1`.

# Exemples

```julia-repl
julia> Threads.threadid()
1

julia> Threads.@threads for i in 1:4
          println(Threads.threadid())
       end
4
2
5
4
```

!!! note
    Le thread sur lequel une tâche s'exécute peut changer si la tâche cède, ce qui est connu sous le nom de [`Task Migration`](@ref man-task-migration). Pour cette raison, dans la plupart des cas, il n'est pas sûr d'utiliser `threadid()` pour indexer, par exemple, un vecteur d'objets tampon ou d'objets à état.

