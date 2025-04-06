```
>(x, y)
```

Größer-als-Vergleichsoperator. Fällt zurück auf `y < x`.

# Implementierung

Im Allgemeinen sollten neue Typen [`<`](@ref) anstelle dieser Funktion implementieren und sich auf die Rückfalldefinition `>(x, y) = y < x` verlassen.

# Beispiele

```jldoctest
julia> 'a' > 'b'
false

julia> 7 > 3 > 1
true

julia> "abc" > "abd"
false

julia> 5 > 3
true
```
