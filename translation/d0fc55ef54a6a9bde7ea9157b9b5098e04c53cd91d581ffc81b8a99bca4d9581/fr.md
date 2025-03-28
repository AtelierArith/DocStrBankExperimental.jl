```
searchsorted(v, x; by=identity, lt=isless, rev=false)
```

Renvoie la plage d'indices dans `v` où les valeurs sont équivalentes à `x`, ou une plage vide située au point d'insertion si `v` ne contient pas de valeurs équivalentes à `x`. Le vecteur `v` doit être trié selon l'ordre défini par les mots-clés. Consultez [`sort!`](@ref) pour la signification des mots-clés et la définition de l'équivalence. Notez que la fonction `by` est appliquée à la valeur recherchée `x` ainsi qu'aux valeurs dans `v`.

La plage est généralement trouvée en utilisant une recherche binaire, mais il existe des implémentations optimisées pour certaines entrées.

Voir aussi : [`searchsortedfirst`](@ref), [`sort!`](@ref), [`insorted`](@ref), [`findall`](@ref).

# Exemples

```jldoctest
julia> searchsorted([1, 2, 4, 5, 5, 7], 4) # correspondance unique
3:3

julia> searchsorted([1, 2, 4, 5, 5, 7], 5) # correspondances multiples
4:5

julia> searchsorted([1, 2, 4, 5, 5, 7], 3) # pas de correspondance, insérer au milieu
3:2

julia> searchsorted([1, 2, 4, 5, 5, 7], 9) # pas de correspondance, insérer à la fin
7:6

julia> searchsorted([1, 2, 4, 5, 5, 7], 0) # pas de correspondance, insérer au début
1:0

julia> searchsorted([1=>"one", 2=>"two", 2=>"two", 4=>"four"], 2=>"two", by=first) # comparer les clés des paires
2:3
```
