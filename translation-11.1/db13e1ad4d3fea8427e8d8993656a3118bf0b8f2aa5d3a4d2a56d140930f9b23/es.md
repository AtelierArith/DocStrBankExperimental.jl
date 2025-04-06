```
cmp(a::AbstractString, b::AbstractString) -> Int
```

Compara dos cadenas. Devuelve `0` si ambas cadenas tienen la misma longitud y el carácter en cada índice es el mismo en ambas cadenas. Devuelve `-1` si `a` es un prefijo de `b`, o si `a` precede a `b` en orden alfabético. Devuelve `1` si `b` es un prefijo de `a`, o si `b` precede a `a` en orden alfabético (técnicamente, orden lexicográfico por puntos de código Unicode).

# Ejemplos

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
