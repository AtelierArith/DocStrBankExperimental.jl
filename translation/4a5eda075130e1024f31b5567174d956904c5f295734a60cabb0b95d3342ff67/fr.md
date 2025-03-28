```
>=(x, y)
≥(x,y)
```

Opérateur de comparaison supérieur ou égal. Se rabat sur `y <= x`.

# Exemples

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
