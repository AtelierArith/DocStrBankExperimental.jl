```
ismutable(v) -> Bool
```

Retourne `true` si et seulement si la valeur `v` est mutable. Voir [Types composites mutables](@ref) pour une discussion sur l'immuabilité. Notez que cette fonction fonctionne sur des valeurs, donc si vous lui donnez un `DataType`, elle vous dira qu'une valeur de ce type est mutable.

!!! note
    Pour des raisons techniques, `ismutable` retourne `true` pour des valeurs de certains types spéciaux (par exemple `String` et `Symbol`) même s'ils ne peuvent pas être mutés de manière permise.


Voir aussi [`isbits`](@ref), [`isstructtype`](@ref).

# Exemples

```jldoctest
julia> ismutable(1)
false

julia> ismutable([1,2])
true
```

!!! compat "Julia 1.5"
    Cette fonction nécessite au moins Julia 1.5.

