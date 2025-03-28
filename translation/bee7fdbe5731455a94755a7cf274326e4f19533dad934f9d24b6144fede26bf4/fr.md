```
searchsortedlast(v, x; by=identity, lt=isless, rev=false)
```

Retourne l'index de la dernière valeur dans `v` qui n'est pas ordonnée après `x`. Si toutes les valeurs dans `v` sont ordonnées après `x`, retourne `firstindex(v) - 1`.

Le vecteur `v` doit être trié selon l'ordre défini par les mots-clés. L'insertion de `x` immédiatement après l'index retourné maintiendra l'ordre trié. Référez-vous à [`sort!`](@ref) pour la signification et l'utilisation des mots-clés. Notez que la fonction `by` est appliquée à la valeur recherchée `x` ainsi qu'aux valeurs dans `v`.

L'index est généralement trouvé en utilisant une recherche binaire, mais il existe des implémentations optimisées pour certaines entrées.

# Exemples

```jldoctest
julia> searchsortedlast([1, 2, 4, 5, 5, 7], 4) # correspondance unique
3

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 5) # correspondances multiples
5

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 3) # pas de correspondance, insérer au milieu
2

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 9) # pas de correspondance, insérer à la fin
6

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 0) # pas de correspondance, insérer au début
0

julia> searchsortedlast([1=>"un", 2=>"deux", 4=>"quatre"], 3=>"trois", by=first) # comparer les clés des paires
2
```
