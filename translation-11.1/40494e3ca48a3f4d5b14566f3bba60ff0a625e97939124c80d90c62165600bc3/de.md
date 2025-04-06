```
occursin(haystack)
```

Erstellen Sie eine Funktion, die überprüft, ob ihr Argument in `haystack` vorkommt, d.h. eine Funktion, die äquivalent zu `needle -> occursin(needle, haystack)` ist.

Die zurückgegebene Funktion hat den Typ `Base.Fix2{typeof(occursin)}`.

!!! compat "Julia 1.6"
    Diese Methode erfordert Julia 1.6 oder höher.


# Beispiele

```jldoctest
julia> search_f = occursin("JuliaLang ist eine Programmiersprache");

julia> search_f("JuliaLang")
true

julia> search_f("Python")
false
```
