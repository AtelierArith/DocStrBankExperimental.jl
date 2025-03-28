```
LazyString <: AbstractString
```

Une représentation paresseuse de l'interpolation de chaînes. Cela est utile lorsqu'une chaîne doit être construite dans un contexte où l'interpolation réelle et la construction de la chaîne sont inutiles ou indésirables (par exemple, dans les chemins d'erreur des fonctions).

Ce type est conçu pour être peu coûteux à construire à l'exécution, essayant de décharger autant de travail que possible soit sur le macro, soit sur les opérations d'impression ultérieures.

# Exemples

```jldoctest
julia> n = 5; str = LazyString("n is ", n)
"n is 5"
```

Voir aussi [`@lazy_str`](@ref).

!!! compat "Julia 1.8"
    `LazyString` nécessite Julia 1.8 ou une version ultérieure.


# Aide étendue

## Propriétés de sécurité pour les programmes concurrents

Une chaîne paresseuse elle-même n'introduit aucun problème de concurrence même si elle est imprimée dans plusieurs tâches Julia. Cependant, si les méthodes `print` sur une valeur capturée peuvent avoir un problème de concurrence lorsqu'elles sont invoquées sans synchronisations, l'impression de la chaîne paresseuse peut poser un problème. De plus, les méthodes `print` sur les valeurs capturées peuvent être invoquées plusieurs fois, bien qu'un seul résultat exact soit retourné.

!!! compat "Julia 1.9"
    `LazyString` est sûr dans ce sens dans Julia 1.9 et versions ultérieures.

