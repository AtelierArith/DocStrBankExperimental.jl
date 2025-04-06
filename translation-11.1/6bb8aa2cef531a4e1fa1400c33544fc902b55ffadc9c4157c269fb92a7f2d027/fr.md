```
ccall((nom_fonction, bibliothèque), type_retour, (type_arg1, ...), valeur_arg1, ...)
ccall(nom_fonction, type_retour, (type_arg1, ...), valeur_arg1, ...)
ccall(pointeur_fonction, type_retour, (type_arg1, ...), valeur_arg1, ...)
```

Appelle une fonction dans une bibliothèque partagée exportée en C, spécifiée par le tuple `(nom_fonction, bibliothèque)`, où chaque composant est soit une chaîne de caractères, soit un symbole. Au lieu de spécifier une bibliothèque, on peut également utiliser un symbole ou une chaîne de caractères `nom_fonction`, qui est résolu dans le processus actuel. Alternativement, `ccall` peut également être utilisé pour appeler un pointeur de fonction `pointeur_fonction`, tel que celui retourné par `dlsym`.

Notez que le tuple de types d'arguments doit être un tuple littéral, et non une variable ou une expression de type tuple.

Chaque `valeur_arg` pour le `ccall` sera convertie au type `argtype` correspondant, par insertion automatique d'appels à `unsafe_convert(argtype, cconvert(argtype, valeur_arg))`. (Voir aussi la documentation pour [`unsafe_convert`](@ref Base.unsafe_convert) et [`cconvert`](@ref Base.cconvert) pour plus de détails.) Dans la plupart des cas, cela se traduit simplement par un appel à `convert(argtype, valeur_arg)`.
