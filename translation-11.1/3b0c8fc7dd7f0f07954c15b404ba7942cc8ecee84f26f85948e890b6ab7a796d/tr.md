```
<=(x, y)
≤(x,y)
```

Küçük veya eşit karşılaştırma operatörü. `(x < y) | (x == y)` ifadesine geri döner.

# Örnekler

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
