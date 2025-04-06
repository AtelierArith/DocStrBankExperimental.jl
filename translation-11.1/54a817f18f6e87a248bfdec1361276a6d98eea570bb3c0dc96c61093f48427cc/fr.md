```
searchsortedfirst(v, x; by=identity, lt=isless, rev=false)
```

Retourne l'index de la première valeur dans `v` qui n'est pas ordonnée avant `x`. Si toutes les valeurs dans `v` sont ordonnées avant `x`, retourne `lastindex(v) + 1`.

Le vecteur `v` doit être trié selon l'ordre défini par les mots-clés. `insert!`ing `x` à l'index retourné maintiendra l'ordre trié. Référez-vous à [`sort!`](@ref) pour la signification et l'utilisation des mots-clés. Notez que la fonction `by` est appliquée à la valeur recherchée `x` ainsi qu'aux valeurs dans `v`.

L'index est généralement trouvé en utilisant une recherche binaire, mais il existe des implémentations optimisées pour certaines entrées.

Voir aussi : [`searchsortedlast`](@ref), [`searchsorted`](@ref), [`findfirst`](@ref).

# Exemples

```jldoctest
julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 4) # correspondance unique
3

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 5) # correspondances multiples
4

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 3) # pas de correspondance, insérer au milieu
3

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 9) # pas de correspondance, insérer à la fin
7

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 0) # pas de correspondance, insérer au début
1

julia> searchsortedfirst([1=>"one", 2=>"two", 4=>"four"], 3=>"three", by=first) # comparer les clés des paires
3
```
