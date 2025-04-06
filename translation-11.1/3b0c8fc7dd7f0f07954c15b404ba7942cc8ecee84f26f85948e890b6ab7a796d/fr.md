```
<=(x, y)
≤(x,y)
```

Opérateur de comparaison inférieur ou égal. Se rabat sur `(x < y) | (x == y)`.

# Exemples

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
