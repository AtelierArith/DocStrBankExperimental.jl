```
@test_nowarn expr
```

Testez si l'évaluation de `expr` produit une sortie [`stderr`](@ref) vide (pas d'avertissements ni d'autres messages). Renvoie le résultat de l'évaluation de `expr`.

Remarque : L'absence d'avertissements générés par `@warn` ne peut pas être testée avec cette macro. Utilisez [`@test_logs`](@ref) à la place.
