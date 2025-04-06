```
isready(c::Channel)
```

Détermine si un [`Channel`](@ref) a une valeur stockée en lui. Retourne immédiatement, ne bloque pas.

Pour les canaux non tamponnés, retourne `true` s'il y a des tâches en attente sur un [`put!`](@ref).

# Exemples

Canal tamponné :

```jldoctest
julia> c = Channel(1);

julia> isready(c)
false

julia> put!(c, 1);

julia> isready(c)
true
```

Canal non tamponné :

```jldoctest
julia> c = Channel();

julia> isready(c)  # aucune tâche en attente pour mettre !
false

julia> task = Task(() -> put!(c, 1));

julia> schedule(task);  # planifier une tâche put !

julia> isready(c)
true
```
