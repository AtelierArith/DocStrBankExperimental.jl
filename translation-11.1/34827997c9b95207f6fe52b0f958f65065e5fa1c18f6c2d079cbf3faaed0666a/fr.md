```
code_lowered(f, types; generated=true, debuginfo=:default)
```

Renvoie un tableau des formes abaissées (IR) pour les méthodes correspondant à la fonction générique donnée et à la signature de type.

Si `generated` est `false`, les instances `CodeInfo` retournées correspondront aux implémentations de secours. Une erreur est levée si aucune implémentation de secours n'existe. Si `generated` est `true`, ces instances `CodeInfo` correspondront aux corps de méthode obtenus en développant les générateurs.

Le mot-clé `debuginfo` contrôle la quantité de métadonnées de code présentes dans la sortie.

Notez qu'une erreur sera levée si `types` ne sont pas des types de feuille lorsque `generated` est `true` et que l'une des méthodes correspondantes est une méthode `@generated`.
