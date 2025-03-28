```
isequal_normalized(s1::AbstractString, s2::AbstractString; casefold=false, stripmark=false, chartransform=identity)
```

Gibt zurück, ob `s1` und `s2` kanonisch äquivalente Unicode-Zeichenfolgen sind. Wenn `casefold=true`, wird die Groß- und Kleinschreibung ignoriert (führt Unicode-Groß-/Kleinschreibung durch); wenn `stripmark=true`, werden diakritische Zeichen und andere kombinierende Zeichen entfernt.

Wie bei [`Unicode.normalize`](@ref) können Sie auch eine beliebige Funktion über das Schlüsselwort `chartransform` übergeben (die `Integer`-Codepunkte auf Codepunkte abbildet), um benutzerdefinierte Normalisierungen durchzuführen, wie z.B. [`Unicode.julia_chartransform`](@ref).

!!! compat "Julia 1.8"
    Die Funktion `isequal_normalized` wurde in Julia 1.8 hinzugefügt.


# Beispiele

Zum Beispiel kann die Zeichenfolge `"noël"` auf zwei kanonisch äquivalente Arten in Unicode konstruiert werden, abhängig davon, ob `"ë"` aus einem einzelnen Codepunkt U+00EB oder aus dem ASCII-Zeichen `'e'` gefolgt von dem kombinierenden Zeichen U+0308 (Trema) gebildet wird.

```jldoctest
julia> s1 = "noël"
"noël"

julia> s2 = "noël"
"noël"

julia> s1 == s2
false

julia> isequal_normalized(s1, s2)
true

julia> isequal_normalized(s1, "noel", stripmark=true)
true

julia> isequal_normalized(s1, "NOËL", casefold=true)
true
```
