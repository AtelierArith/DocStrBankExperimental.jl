```
methods(f, [types], [module])
```

Retourne la table des méthodes pour `f`.

Si `types` est spécifié, retourne un tableau de méthodes dont les types correspondent. Si `module` est spécifié, retourne un tableau de méthodes définies dans ce module. Une liste de modules peut également être spécifiée sous forme de tableau.

!!! compat "Julia 1.4"
    Au moins Julia 1.4 est requis pour spécifier un module.


Voir aussi : [`which`](@ref), [`@which`](@ref Main.InteractiveUtils.@which) et [`methodswith`](@ref Main.InteractiveUtils.methodswith).
