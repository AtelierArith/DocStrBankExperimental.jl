```
put!(c::Channel, v)
```

Ajoute un élément `v` au canal `c`. Bloque si le canal est plein.

Pour les canaux non tamponnés, bloque jusqu'à ce qu'un [`take!`](@ref) soit effectué par une autre tâche.

!!! compat "Julia 1.1"
    `v` est maintenant converti au type du canal avec [`convert`](@ref) lorsque `put!` est appelé.

