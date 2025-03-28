```
Threads.@spawn [:default|:interactive] expr
```

Créez une [`Task`](@ref) et [`schedule`](@ref) pour l'exécuter sur n'importe quel thread disponible dans le pool de threads spécifié (`:default` si non spécifié). La tâche est allouée à un thread une fois qu'un devient disponible. Pour attendre que la tâche se termine, appelez [`wait`](@ref) sur le résultat de cette macro, ou appelez [`fetch`](@ref) pour attendre puis obtenir sa valeur de retour.

Des valeurs peuvent être interpolées dans `@spawn` via `$`, ce qui copie la valeur directement dans la fermeture sous-jacente construite. Cela vous permet d'insérer la *valeur* d'une variable, isolant le code asynchrone des changements de la valeur de la variable dans la tâche actuelle.

!!! note
    Le thread sur lequel la tâche s'exécute peut changer si la tâche cède, par conséquent `threadid()` ne doit pas être considéré comme constant pour une tâche. Voir [`Task Migration`](@ref man-task-migration), et le manuel plus large sur [multi-threading](@ref man-multithreading) pour d'autres mises en garde importantes. Voir aussi le chapitre sur [threadpools](@ref man-threadpools).


!!! compat "Julia 1.3"
    Cette macro est disponible depuis Julia 1.3.


!!! compat "Julia 1.4"
    L'interpolation de valeurs via `$` est disponible depuis Julia 1.4.


!!! compat "Julia 1.9"
    Un pool de threads peut être spécifié depuis Julia 1.9.


# Exemples

```julia-repl
julia> t() = println("Hello from ", Threads.threadid());

julia> tasks = fetch.([Threads.@spawn t() for i in 1:4]);
Hello from 1
Hello from 1
Hello from 3
Hello from 4
```
