```
endswith(suffix)
```

Erstellen Sie eine Funktion, die überprüft, ob ihr Argument mit `suffix` endet, d.h. eine Funktion, die äquivalent zu `y -> endswith(y, suffix)` ist.

Die zurückgegebene Funktion hat den Typ `Base.Fix2{typeof(endswith)}`, der verwendet werden kann, um spezialisierte Methoden zu implementieren.

!!! compat "Julia 1.5"
    Das Einzelargument `endswith(suffix)` erfordert mindestens Julia 1.5.


# Beispiele

```jldoctest
julia> endswith("Julia")("Ends with Julia")
true

julia> endswith("Julia")("JuliaLang")
false
```
