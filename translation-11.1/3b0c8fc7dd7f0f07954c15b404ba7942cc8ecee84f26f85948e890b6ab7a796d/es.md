```
<=(x, y)
≤(x,y)
```

Operador de comparación menor o igual. Recurre a `(x < y) | (x == y)`.

# Ejemplos

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
