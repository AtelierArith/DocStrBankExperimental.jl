```
detect_ambiguities(mod1, mod2...; recursive=false,
                                  ambiguous_bottom=false,
                                  allowed_undefineds=nothing)
```

Renvoie un vecteur de paires `(Method,Method)` de méthodes ambiguës définies dans les modules spécifiés. Utilisez `recursive=true` pour tester dans tous les sous-modules.

`ambiguous_bottom` contrôle si les ambiguïtés déclenchées uniquement par des paramètres de type `Union{}` sont incluses ; dans la plupart des cas, vous voudrez probablement définir cela sur `false`. Voir [`Base.isambiguous`](@ref).

Voir [`Test.detect_unbound_args`](@ref) pour une explication de `allowed_undefineds`.

!!! compat "Julia 1.8"
    `allowed_undefineds` nécessite au moins Julia 1.8.

