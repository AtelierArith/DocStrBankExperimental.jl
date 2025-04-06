```
<(x, y)
```

Weniger-als-Vergleichsoperator. Fällt zurück auf [`isless`](@ref). Aufgrund des Verhaltens von Gleitkomma-NaN-Werten implementiert dieser Operator eine partielle Ordnung.

# Implementierung

Neue Typen mit einer kanonischen partiellen Ordnung sollten diese Funktion für zwei Argumente des neuen Typs implementieren. Typen mit einer kanonischen totalen Ordnung sollten stattdessen [`isless`](@ref) implementieren.

Siehe auch [`isunordered`](@ref).

# Beispiele

```jldoctest
julia> 'a' < 'b'
true

julia> "abc" < "abd"
true

julia> 5 < 3
false
```
