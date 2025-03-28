```
bind(chnl::Channel, task::Task)
```

Associe la durée de vie de `chnl` à une tâche. Le `Channel` `chnl` est automatiquement fermé lorsque la tâche se termine. Toute exception non interceptée dans la tâche est propagée à tous les attendus sur `chnl`.

L'objet `chnl` peut être explicitement fermé indépendamment de la terminaison de la tâche. Les tâches terminées n'ont aucun effet sur les objets `Channel` déjà fermés.

Lorsqu'un canal est lié à plusieurs tâches, la première tâche à se terminer fermera le canal. Lorsque plusieurs canaux sont liés à la même tâche, la terminaison de la tâche fermera tous les canaux liés.

# Exemples

```jldoctest
julia> c = Channel(0);

julia> task = @async foreach(i->put!(c, i), 1:4);

julia> bind(c,task);

julia> for i in c
           @show i
       end;
i = 1
i = 2
i = 3
i = 4

julia> isopen(c)
false
```

```jldoctest
julia> c = Channel(0);

julia> task = @async (put!(c, 1); error("foo"));

julia> bind(c, task);

julia> take!(c)
1

julia> put!(c, 1);
ERROR: TaskFailedException
Stacktrace:
[...]
    nested task error: foo
[...]
```
