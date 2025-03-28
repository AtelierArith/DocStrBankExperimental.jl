```
take!(c::Channel)
```

Supprime et renvoie une valeur d'un [`Channel`](@ref) dans l'ordre. Bloque jusqu'à ce que des données soient disponibles. Pour les canaux non tamponnés, bloque jusqu'à ce qu'un [`put!`](@ref) soit effectué par une autre tâche.

# Exemples

Canal tamponné :

```jldoctest
julia> c = Channel(1);

julia> put!(c, 1);

julia> take!(c)
1
```

Canal non tamponné :

```jldoctest
julia> c = Channel(0);

julia> task = Task(() -> put!(c, 1));

julia> schedule(task);

julia> take!(c)
1
```
