```
!=(x, y)
≠(x,y)
```

Ungleichheitsvergleichsoperator. Gibt immer die entgegengesetzte Antwort wie [`==`](@ref) zurück.

# Implementierung

Neue Typen sollten dies im Allgemeinen nicht implementieren und stattdessen auf die Fallback-Definition `!=(x,y) = !(x==y)` zurückgreifen.

# Beispiele

```jldoctest
julia> 3 != 2
true

julia> "foo" ≠ "foo"
false
```
