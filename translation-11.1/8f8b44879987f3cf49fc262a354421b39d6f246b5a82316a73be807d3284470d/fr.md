```
which(f, types)
```

Renvoie la méthode de `f` (un objet `Method`) qui serait appelée pour des arguments des `types` donnés.

Si `types` est un type abstrait, alors la méthode qui serait appelée par `invoke` est renvoyée.

Voir aussi : [`parentmodule`](@ref), [`@which`](@ref Main.InteractiveUtils.@which), et [`@edit`](@ref Main.InteractiveUtils.@edit).
