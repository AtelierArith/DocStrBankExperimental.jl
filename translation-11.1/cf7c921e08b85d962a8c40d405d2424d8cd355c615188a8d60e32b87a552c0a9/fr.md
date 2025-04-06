```
dlopen(libfile::AbstractString [, flags::Integer]; throw_error:Bool = true)
```

Charge une bibliothèque partagée, renvoyant un handle opaque.

L'extension donnée par la constante `dlext` (`.so`, `.dll` ou `.dylib`) peut être omise de la chaîne `libfile`, car elle est automatiquement ajoutée si nécessaire. Si `libfile` n'est pas un nom de chemin absolu, alors les chemins dans le tableau `DL_LOAD_PATH` sont recherchés pour `libfile`, suivis du chemin de chargement système.

L'argument facultatif flags est un ou exclusif de zéro ou plusieurs de `RTLD_LOCAL`, `RTLD_GLOBAL`, `RTLD_LAZY`, `RTLD_NOW`, `RTLD_NODELETE`, `RTLD_NOLOAD`, `RTLD_DEEPBIND` et `RTLD_FIRST`. Ceux-ci sont convertis en les drapeaux correspondants de la commande dlopen POSIX (et/ou GNU libc et/ou MacOS), si possible, ou sont ignorés si la fonctionnalité spécifiée n'est pas disponible sur la plateforme actuelle. Les drapeaux par défaut sont spécifiques à la plateforme. Sur MacOS, les drapeaux par défaut de `dlopen` sont `RTLD_LAZY|RTLD_DEEPBIND|RTLD_GLOBAL`, tandis que sur d'autres plateformes, les valeurs par défaut sont `RTLD_LAZY|RTLD_DEEPBIND|RTLD_LOCAL`. Une utilisation importante de ces drapeaux est de spécifier un comportement non par défaut pour lorsque le chargeur de bibliothèque dynamique lie des références de bibliothèque à des symboles exportés et si les références liées sont mises dans un scope local au processus ou global. Par exemple, `RTLD_LAZY|RTLD_DEEPBIND|RTLD_GLOBAL` permet aux symboles de la bibliothèque d'être disponibles pour une utilisation dans d'autres bibliothèques partagées, abordant des situations où il y a des dépendances entre les bibliothèques partagées.

Si la bibliothèque ne peut pas être trouvée, cette méthode lance une erreur, sauf si l'argument clé `throw_error` est défini sur `false`, auquel cas cette méthode renvoie `nothing`.

!!! note
    À partir de Julia 1.6, cette méthode remplace les chemins commençant par `@executable_path/` par le chemin vers l'exécutable Julia, permettant des chargements de chemins relatifs relocalisables. Dans Julia 1.5 et antérieur, cela ne fonctionnait que sur macOS.

