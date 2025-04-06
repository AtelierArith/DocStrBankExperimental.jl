```
>=(x, y)
≥(x,y)
```

Größer-als-oder-gleich Vergleichsoperator. Fällt zurück auf `y <= x`.

# Beispiele

```jldoctest
julia> 'a' >= 'b'
false

julia> 7 ≥ 7 ≥ 3
true

julia> "abc" ≥ "abc"
true

julia> 5 >= 3
true
```
