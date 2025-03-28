```
addenv(command::Cmd, env...; inherit::Bool = true)
```

Fusionne de nouvelles mappages d'environnement dans l'objet [`Cmd`](@ref) donné, retournant un nouvel objet `Cmd`. Les clés en double sont remplacées. Si `command` ne contient pas déjà de valeurs d'environnement, il hérite de l'environnement actuel au moment de l'appel de `addenv()` si `inherit` est `true`. Les clés avec la valeur `nothing` sont supprimées de l'environnement.

Voir aussi [`Cmd`](@ref), [`setenv`](@ref), [`ENV`](@ref).

!!! compat "Julia 1.6"
    Cette fonction nécessite Julia 1.6 ou une version ultérieure.

