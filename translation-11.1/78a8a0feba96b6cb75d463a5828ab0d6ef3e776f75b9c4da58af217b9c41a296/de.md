```
startswith(prefix)
```

Erstellen Sie eine Funktion, die überprüft, ob ihr Argument mit `prefix` beginnt, d.h. eine Funktion, die äquivalent zu `y -> startswith(y, prefix)` ist.

Die zurückgegebene Funktion hat den Typ `Base.Fix2{typeof(startswith)}`, der verwendet werden kann, um spezialisierte Methoden zu implementieren.

!!! compat "Julia 1.5"
    Das Einzelargument `startswith(prefix)` erfordert mindestens Julia 1.5.


# Beispiele

```jldoctest
julia> startswith("Julia")("JuliaLang")
true

julia> startswith("Julia")("Ends with Julia")
false
```
