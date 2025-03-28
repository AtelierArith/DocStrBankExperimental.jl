```
checkindex(Bool, inds::AbstractUnitRange, index)
```

Gibt `true` zurück, wenn der angegebene `index` innerhalb der Grenzen von `inds` liegt. Benutzerdefinierte Typen, die sich wie Indizes für alle Arrays verhalten möchten, können diese Methode erweitern, um eine spezialisierte Implementierung der Bereichsüberprüfung bereitzustellen.

Siehe auch [`checkbounds`](@ref).

# Beispiele

```jldoctest
julia> checkindex(Bool, 1:20, 8)
true

julia> checkindex(Bool, 1:20, 21)
false
```
