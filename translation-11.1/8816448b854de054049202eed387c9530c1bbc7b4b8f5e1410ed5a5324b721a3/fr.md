```
randjump(r::MersenneTwister, steps::Integer) -> MersenneTwister
```

Créez un objet `MersenneTwister` initialisé, dont l'état est avancé (sans générer de nombres) à partir de `r` de `steps` étapes. Une telle étape correspond à la génération de deux nombres `Float64`. Pour chaque valeur différente de `steps`, un grand polynôme doit être généré en interne. Un est déjà pré-calculé pour `steps=big(10)^20`.
