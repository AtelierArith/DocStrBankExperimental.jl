```
cmp(a::AbstractString, b::AbstractString) -> Int
```

Vergleiche zwei Strings. Gib `0` zurück, wenn beide Strings die gleiche Länge haben und das Zeichen an jedem Index in beiden Strings gleich ist. Gib `-1` zurück, wenn `a` ein Präfix von `b` ist oder wenn `a` alphabetisch vor `b` kommt. Gib `1` zurück, wenn `b` ein Präfix von `a` ist oder wenn `b` alphabetisch vor `a` kommt (technisch gesehen, lexikografische Reihenfolge nach Unicode-Codepunkten).

# Beispiele

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
