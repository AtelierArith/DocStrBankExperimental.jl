```
rmprocs(pids...; waitfor=typemax(Int))
```

Supprime les travailleurs spécifiés. Notez que seul le processus 1 peut ajouter ou supprimer des travailleurs.

L'argument `waitfor` spécifie combien de temps attendre que les travailleurs s'arrêtent :

  * Si non spécifié, `rmprocs` attendra que tous les `pids` demandés soient supprimés.
  * Une [`ErrorException`](@ref) est levée si tous les travailleurs ne peuvent pas être terminés avant les secondes `waitfor` demandées.
  * Avec une valeur `waitfor` de 0, l'appel retourne immédiatement avec les travailleurs programmés pour suppression dans une tâche différente. L'objet [`Task`](@ref) programmé est retourné. L'utilisateur doit appeler [`wait`](@ref) sur la tâche avant d'invoquer d'autres appels parallèles.

# Exemples

```julia-repl
$ julia -p 5

julia> t = rmprocs(2, 3, waitfor=0)
Task (runnable) @0x0000000107c718d0

julia> wait(t)

julia> workers()
3-element Array{Int64,1}:
 4
 5
 6
```
