```
modifyproperty!(x, f::Symbol, op, v, order::Symbol=:not_atomic)
```

La syntaxe `@atomic op(x.f, v)` (et son équivalent `@atomic x.f op v`) renvoie `modifyproperty!(x, :f, op, v, :sequentially_consistent)`, où le premier argument doit être une expression `getproperty` et est modifié de manière atomique.

L'invocation de `op(getproperty(x, f), v)` doit renvoyer une valeur qui peut être stockée dans le champ `f` de l'objet `x` par défaut. En particulier, contrairement au comportement par défaut de [`setproperty!`](@ref Base.setproperty!), la fonction `convert` n'est pas appelée automatiquement.

Voir aussi [`modifyfield!`](@ref Core.modifyfield!) et [`setproperty!`](@ref Base.setproperty!).
