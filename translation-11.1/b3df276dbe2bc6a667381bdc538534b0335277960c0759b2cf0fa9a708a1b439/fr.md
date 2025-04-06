```
Base.isprecompiled(pkg::PkgId; ignore_loaded::Bool=false)
```

Renvoie si un PkgId donné dans le projet actif est précompilé.

Par défaut, cette vérification observe la même approche que le chargement de code en ce qui concerne les différentes versions des dépendances actuellement chargées par rapport à ce qui est attendu. Pour ignorer les modules chargés et répondre comme si vous étiez dans une nouvelle session julia, spécifiez `ignore_loaded=true`.

!!! compat "Julia 1.10"
    Cette fonction nécessite au moins Julia 1.10.

