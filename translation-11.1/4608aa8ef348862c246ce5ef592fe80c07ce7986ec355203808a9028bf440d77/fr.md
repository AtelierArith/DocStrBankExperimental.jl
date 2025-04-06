```
isempty(collection) -> Bool
```

Déterminez si une collection est vide (n'a aucun élément).

!!! avertissement
    `isempty(itr)` peut consommer le prochain élément d'un itérateur à état `itr` à moins qu'une méthode appropriée [`Base.isdone(itr)`](@ref) ne soit définie. Les itérateurs à état *devraient* implémenter `isdone`, mais vous voudrez peut-être éviter d'utiliser `isempty` lors de l'écriture de code générique qui devrait prendre en charge tout type d'itérateur.


# Exemples

```jldoctest
julia> isempty([])
true

julia> isempty([1 2 3])
false
```
