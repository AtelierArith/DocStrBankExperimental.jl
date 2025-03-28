```
isimmutable(v) -> Bool
```

!!! warning
    Envisagez d'utiliser `!ismutable(v)` à la place, car `isimmutable(v)` sera remplacé par `!ismutable(v)` dans une future version. (Depuis Julia 1.5)


Retourne `true` si et seulement si la valeur `v` est immuable. Voir [Mutable Composite Types](@ref) pour une discussion sur l'immuabilité. Notez que cette fonction fonctionne sur des valeurs, donc si vous lui donnez un type, elle vous dira qu'une valeur de `DataType` est mutable.

# Exemples

```jldoctest
julia> isimmutable(1)
true

julia> isimmutable([1,2])
false
```
