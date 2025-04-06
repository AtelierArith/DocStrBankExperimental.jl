```
cmp(a::AbstractString, b::AbstractString) -> Int
```

İki dizeyi karşılaştır. Her iki dize de aynı uzunluktaysa ve her bir indeksteki karakterler her iki dizede de aynıysa `0` döndür. `a`, `b`'nin ön eki ise veya `a`, `b`'den alfabetik sırada önce geliyorsa `-1` döndür. `b`, `a`'nın ön eki ise veya `b`, `a`'dan alfabetik sırada önce geliyorsa (teknik olarak, Unicode kod noktalarına göre leksikografik sırada) `1` döndür.

# Örnekler

```jldoctest
julia> cmp("abc", "abc")
0

julia> cmp("ab", "abc")
-1

julia> cmp("abc", "ab")
1

julia> cmp("ab", "ac")
-1

julia> cmp("ac", "ab")
1

julia> cmp("α", "a")
1

julia> cmp("b", "β")
-1
```
