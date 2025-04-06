```
@test_warn msg expr
```

Testez si l'évaluation de `expr` produit une sortie [`stderr`](@ref) qui contient la chaîne `msg` ou correspond à l'expression régulière `msg`. Si `msg` est une fonction booléenne, teste si `msg(output)` renvoie `true`. Si `msg` est un tuple ou un tableau, vérifie que la sortie d'erreur contient/correspond à chaque élément de `msg`. Renvoie le résultat de l'évaluation de `expr`.

Voir aussi [`@test_nowarn`](@ref) pour vérifier l'absence de sortie d'erreur.

Remarque : Les avertissements générés par `@warn` ne peuvent pas être testés avec cette macro. Utilisez [`@test_logs`](@ref) à la place.
