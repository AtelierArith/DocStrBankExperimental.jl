```
insorted(x, v; by=identity, lt=isless, rev=false) -> Bool
```

Déterminez si un vecteur `v` contient une valeur équivalente à `x`. Le vecteur `v` doit être trié selon l'ordre défini par les mots-clés. Référez-vous à [`sort!`](@ref) pour la signification des mots-clés et la définition de l'équivalence. Notez que la fonction `by` est appliquée à la valeur recherchée `x` ainsi qu'aux valeurs dans `v`.

La vérification est généralement effectuée à l'aide d'une recherche binaire, mais il existe des implémentations optimisées pour certaines entrées.

Voir aussi [`in`](@ref).

# Exemples

```jldoctest
julia> insorted(4, [1, 2, 4, 5, 5, 7]) # correspondance unique
true

julia> insorted(5, [1, 2, 4, 5, 5, 7]) # correspondances multiples
true

julia> insorted(3, [1, 2, 4, 5, 5, 7]) # pas de correspondance
false

julia> insorted(9, [1, 2, 4, 5, 5, 7]) # pas de correspondance
false

julia> insorted(0, [1, 2, 4, 5, 5, 7]) # pas de correspondance
false

julia> insorted(2=>"TWO", [1=>"one", 2=>"two", 4=>"four"], by=first) # comparer les clés des paires
true
```

!!! compat "Julia 1.6"
    `insorted` a été ajouté dans Julia 1.6.

