```
include([mapexpr::Function,] path::AbstractString)
```

Évalue le contenu du fichier source d'entrée dans le scope global du module contenant. Chaque module (sauf ceux définis avec `baremodule`) a sa propre définition de `include`, qui évalue le fichier dans ce module. Renvoie le résultat de la dernière expression évaluée du fichier d'entrée. Lors de l'inclusion, un chemin d'inclusion local à la tâche est défini sur le répertoire contenant le fichier. Les appels imbriqués à `include` rechercheront par rapport à ce chemin. Cette fonction est généralement utilisée pour charger du code source de manière interactive, ou pour combiner des fichiers dans des packages qui sont divisés en plusieurs fichiers source. L'argument `path` est normalisé à l'aide de [`normpath`](@ref) qui résoudra les tokens de chemin relatifs tels que `..` et convertira `/` en le séparateur de chemin approprié.

L'argument optionnel `mapexpr` peut être utilisé pour transformer le code inclus avant qu'il ne soit évalué : pour chaque expression analysée `expr` dans `path`, la fonction `include` évalue en réalité `mapexpr(expr)`. S'il est omis, `mapexpr` par défaut à [`identity`](@ref).

Utilisez [`Base.include`](@ref) pour évaluer un fichier dans un autre module.

!!! compat "Julia 1.5"
    Julia 1.5 est requise pour passer l'argument `mapexpr`.

