```
reverse(s::AbstractString) -> AbstractString
```

Kehrt einen String um. Technisch gesehen kehrt diese Funktion die Codepunkte in einem String um und ihre Hauptnützlichkeit liegt in der Verarbeitung von Strings in umgekehrter Reihenfolge, insbesondere bei umgekehrten regulären Ausdruckssuchen. Siehe auch [`reverseind`](@ref), um Indizes in `s` in Indizes in `reverse(s)` und umgekehrt zu konvertieren, sowie `graphemes` aus dem Modul `Unicode`, um auf benutzerlich sichtbare "Zeichen" (Grapheme) anstelle von Codepunkten zu operieren. Siehe auch [`Iterators.reverse`](@ref) für die Iteration in umgekehrter Reihenfolge, ohne eine Kopie zu erstellen. Benutzerdefinierte String-Typen müssen die Funktion `reverse` selbst implementieren und sollten typischerweise einen String mit demselben Typ und derselben Kodierung zurückgeben. Wenn sie einen String mit einer anderen Kodierung zurückgeben, müssen sie auch `reverseind` für diesen String-Typ überschreiben, um `s[reverseind(s,i)] == reverse(s)[i]` zu erfüllen.

# Beispiele

```jldoctest
julia> reverse("JuliaLang")
"gnaLailuJ"
```

!!! Hinweis     Die folgenden Beispiele können auf verschiedenen Systemen unterschiedlich gerendert werden. Die Kommentare geben an, wie sie gerendert werden sollen.

Kombinierende Zeichen können zu überraschenden Ergebnissen führen:

```jldoctest
julia> reverse("ax̂e") # Der Hut ist über x im Eingabewert, über e im Ausgabewert
"êxa"

julia> using Unicode

julia> join(reverse(collect(graphemes("ax̂e")))) # kehrt Grapheme um; der Hut ist über x in beiden Eingabe- und Ausgabewerten
"ex̂a"
```
