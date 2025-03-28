```
<=(x, y)
≤(x,y)
```

Weniger-als-oder-gleich Vergleichsoperator. Fällt zurück auf `(x < y) | (x == y)`.

# Beispiele

```jldoctest
julia> 'a' <= 'b'
true

julia> 7 ≤ 7 ≤ 9
true

julia> "abc" ≤ "abc"
true

julia> 5 <= 3
false
```
