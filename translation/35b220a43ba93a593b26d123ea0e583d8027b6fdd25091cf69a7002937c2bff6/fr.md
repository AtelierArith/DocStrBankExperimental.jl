```
set_zero_subnormals(yes::Bool) -> Bool
```

Si `yes` est `false`, les opérations en virgule flottante suivantes suivent les règles de l'arithmétique IEEE sur les valeurs subnormales ("denormals"). Sinon, les opérations en virgule flottante sont autorisées (mais pas obligatoires) à convertir les entrées ou sorties subnormales en zéro. Renvoie `true` sauf si `yes==true` mais le matériel ne prend pas en charge la mise à zéro des nombres subnormaux.

`set_zero_subnormals(true)` peut accélérer certains calculs sur certains matériels. Cependant, cela peut rompre des identités telles que `(x-y==0) == (x==y)`.

!!! avertissement
    Cette fonction n'affecte que le thread actuel.

