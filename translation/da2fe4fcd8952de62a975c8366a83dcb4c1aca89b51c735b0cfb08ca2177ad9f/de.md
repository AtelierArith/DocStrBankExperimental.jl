```
chopsuffix(s::AbstractString, suffix::Union{AbstractString,Regex}) -> SubString
```

Entfernt das Suffix `suffix` von `s`. Wenn `s` nicht mit `suffix` endet, wird ein String, der `s` entspricht, zurückgegeben.

Siehe auch [`chopprefix`](@ref).

!!! compat "Julia 1.8"
    Diese Funktion ist seit Julia 1.8 verfügbar.


# Beispiele

```jldoctest
julia> chopsuffix("Hamburger", "er")
"Hamburg"

julia> chopsuffix("Hamburger", "hotdog")
"Hamburger"
```
