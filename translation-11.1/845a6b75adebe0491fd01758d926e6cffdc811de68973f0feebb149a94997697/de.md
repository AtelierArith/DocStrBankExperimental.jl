```
filter(f)
```

Erstellen Sie eine Funktion, die ihre Argumente mit der Funktion `f` unter Verwendung von [`filter`](@ref) filtert, d.h. eine Funktion, die äquivalent zu `x -> filter(f, x)` ist.

Die zurückgegebene Funktion ist vom Typ `Base.Fix1{typeof(filter)}`, die verwendet werden kann, um spezialisierte Methoden zu implementieren.

# Beispiele

```jldoctest
julia> (1, 2, Inf, 4, NaN, 6) |> filter(isfinite)
(1, 2, 4, 6)

julia> map(filter(iseven), [1:3, 2:4, 3:5])
3-element Vector{Vector{Int64}}:
 [2]
 [2, 4]
 [4]
```

!!! compat "Julia 1.9"
    Diese Methode erfordert mindestens Julia 1.9.

