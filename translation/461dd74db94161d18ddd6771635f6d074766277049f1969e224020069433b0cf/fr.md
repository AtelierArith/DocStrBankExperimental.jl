```
setrounding(T, mode)
```

Définir le mode d'arrondi du type de point flottant `T`, contrôlant l'arrondi des fonctions arithmétiques de base ([`+`](@ref), [`-`](@ref), [`*`](@ref), [`/`](@ref) et [`sqrt`](@ref)) et la conversion de type. D'autres fonctions numériques peuvent donner des valeurs incorrectes ou invalides lors de l'utilisation de modes d'arrondi autres que le mode par défaut [`RoundNearest`](@ref).

Notez que cela n'est actuellement pris en charge que pour `T == BigFloat`.

!!! avertissement
    Cette fonction n'est pas sûre pour les threads. Elle affectera le code s'exécutant sur tous les threads, mais son comportement est indéfini si elle est appelée simultanément avec des calculs utilisant le paramètre.

