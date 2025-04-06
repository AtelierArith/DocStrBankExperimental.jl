```
Base.include([mapexpr::Function,] m::Module, path::AbstractString)
```

Évalue le contenu du fichier source d'entrée dans le scope global du module `m`. Chaque module (sauf ceux définis avec [`baremodule`](@ref)) a sa propre définition de `include` omettant l'argument `m`, qui évalue le fichier dans ce module. Renvoie le résultat de la dernière expression évaluée du fichier d'entrée. Lors de l'inclusion, un chemin d'inclusion local à la tâche est défini sur le répertoire contenant le fichier. Les appels imbriqués à `include` rechercheront par rapport à ce chemin. Cette fonction est généralement utilisée pour charger le code source de manière interactive, ou pour combiner des fichiers dans des packages qui sont divisés en plusieurs fichiers source.

L'argument optionnel `mapexpr` peut être utilisé pour transformer le code inclus avant qu'il ne soit évalué : pour chaque expression analysée `expr` dans `path`, la fonction `include` évalue en réalité `mapexpr(expr)`. Si elle est omise, `mapexpr` par défaut à [`identity`](@ref).

!!! compat "Julia 1.5"
    Julia 1.5 est requise pour passer l'argument `mapexpr`.

