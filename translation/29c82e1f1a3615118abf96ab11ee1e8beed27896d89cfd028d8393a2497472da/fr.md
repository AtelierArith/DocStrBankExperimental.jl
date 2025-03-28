```
detect_unbound_args(mod1, mod2...; recursive=false, allowed_undefineds=nothing)
```

Renvoie un vecteur de `Method`s qui peuvent avoir des paramètres de type non liés. Utilisez `recursive=true` pour tester dans tous les sous-modules.

Par défaut, tout symbole non défini déclenche un avertissement. Cet avertissement peut être supprimé en fournissant une collection de `GlobalRef`s pour lesquels l'avertissement peut être ignoré. Par exemple, en définissant

```
allowed_undefineds = Set([GlobalRef(Base, :active_repl),
                          GlobalRef(Base, :active_repl_backend)])
```

vous supprimeriez les avertissements concernant `Base.active_repl` et `Base.active_repl_backend`.

!!! compat "Julia 1.8"
    `allowed_undefineds` nécessite au moins Julia 1.8.

