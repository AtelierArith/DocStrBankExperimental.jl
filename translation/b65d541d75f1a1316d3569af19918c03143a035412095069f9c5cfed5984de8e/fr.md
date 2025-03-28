```
Channel{T=Any}(func::Function, size=0; taskref=nothing, spawn=false, threadpool=nothing)
```

Créez une nouvelle tâche à partir de `func`, liez-la à un nouveau canal de type `T` et de taille `size`, et planifiez la tâche, le tout en un seul appel. Le canal est automatiquement fermé lorsque la tâche se termine.

`func` doit accepter le canal lié comme son seul argument.

Si vous avez besoin d'une référence à la tâche créée, passez un objet `Ref{Task}` via l'argument clé `taskref`.

Si `spawn=true`, la `Task` créée pour `func` peut être planifiée sur un autre thread en parallèle, équivalent à la création d'une tâche via [`Threads.@spawn`](@ref).

Si `spawn=true` et que l'argument `threadpool` n'est pas défini, il par défaut à `:default`.

Si l'argument `threadpool` est défini (à `:default` ou `:interactive`), cela implique que `spawn=true` et la nouvelle tâche est lancée dans le threadpool spécifié.

Retourne un `Channel`.

# Exemples

```jldoctest
julia> chnl = Channel() do ch
           foreach(i -> put!(ch, i), 1:4)
       end;

julia> typeof(chnl)
Channel{Any}

julia> for i in chnl
           @show i
       end;
i = 1
i = 2
i = 3
i = 4
```

Référencer la tâche créée :

```jldoctest
julia> taskref = Ref{Task}();

julia> chnl = Channel(taskref=taskref) do ch
           println(take!(ch))
       end;

julia> istaskdone(taskref[])
false

julia> put!(chnl, "Hello");
Hello

julia> istaskdone(taskref[])
true
```

!!! compat "Julia 1.3"
    Le paramètre `spawn=` a été ajouté dans Julia 1.3. Ce constructeur a été ajouté dans Julia 1.3. Dans les versions antérieures de Julia, Channel utilisait des arguments clés pour définir `size` et `T`, mais ces constructeurs sont obsolètes.


!!! compat "Julia 1.9"
    L'argument `threadpool=` a été ajouté dans Julia 1.9.


```jldoctest
julia> chnl = Channel{Char}(1, spawn=true) do ch
           for c in "hello world"
               put!(ch, c)
           end
       end
Channel{Char}(1) (2 items available)

julia> String(collect(chnl))
"hello world"
```
