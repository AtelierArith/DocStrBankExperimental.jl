```
cmp(a::AbstractString, b::AbstractString) -> Int
```

Comparer deux chaînes. Retourner `0` si les deux chaînes ont la même longueur et que le caractère à chaque index est le même dans les deux chaînes. Retourner `-1` si `a` est un préfixe de `b`, ou si `a` vient avant `b` dans l'ordre alphabétique. Retourner `1` si `b` est un préfixe de `a`, ou si `b` vient avant `a` dans l'ordre alphabétique (techniquement, l'ordre lexicographique par points de code Unicode).

# Exemples

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
