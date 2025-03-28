```
chopprefix(s::AbstractString, prefix::Union{AbstractString,Regex}) -> SubString
```

Entfernt das Präfix `prefix` von `s`. Wenn `s` nicht mit `prefix` beginnt, wird ein String, der `s` entspricht, zurückgegeben.

Siehe auch [`chopsuffix`](@ref).

!!! compat "Julia 1.8"
    Diese Funktion ist seit Julia 1.8 verfügbar.


# Beispiele

```jldoctest
julia> chopprefix("Hamburger", "Ham")
"burger"

julia> chopprefix("Hamburger", "hotdog")
"Hamburger"
```
