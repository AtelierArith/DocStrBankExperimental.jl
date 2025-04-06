```
setprecision([T=BigFloat,] precision::Int; base=2)
```

Définissez la précision (en bits, par défaut) à utiliser pour l'arithmétique de `T`. Si `base` est spécifié, alors la précision est le minimum requis pour donner au moins `precision` chiffres dans la base donnée.

!!! avertissement
    Cette fonction n'est pas sûre pour les threads. Elle affectera le code s'exécutant sur tous les threads, mais son comportement est indéfini si elle est appelée simultanément avec des calculs qui utilisent le paramètre.


!!! compat "Julia 1.8"
    Le mot-clé `base` nécessite au moins Julia 1.8.

