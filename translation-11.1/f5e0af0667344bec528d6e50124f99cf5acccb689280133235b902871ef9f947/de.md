```
include([mapexpr::Function,] path::AbstractString)
```

Bewerten Sie den Inhalt der Eingabedatei im globalen Geltungsbereich des umschließenden Moduls. Jedes Modul (außer den mit `baremodule` definierten) hat seine eigene Definition von `include`, die die Datei in diesem Modul auswertet. Gibt das Ergebnis des letzten ausgewerteten Ausdrucks der Eingabedatei zurück. Während des Einschlusses wird ein aufgabenlokaler Einschluss-Pfad auf das Verzeichnis gesetzt, das die Datei enthält. Verschachtelte Aufrufe von `include` suchen relativ zu diesem Pfad. Diese Funktion wird typischerweise verwendet, um Quellcode interaktiv zu laden oder um Dateien in Paketen zu kombinieren, die in mehrere Quelldateien aufgeteilt sind. Das Argument `path` wird mit [`normpath`](@ref) normalisiert, was relative Pfad-Tokens wie `..` auflöst und `/` in den entsprechenden Pfadtrennzeichen umwandelt.

Das optionale erste Argument `mapexpr` kann verwendet werden, um den eingeschlossenen Code zu transformieren, bevor er ausgewertet wird: für jeden geparsten Ausdruck `expr` in `path` wertet die Funktion `include` tatsächlich `mapexpr(expr)` aus. Wenn es weggelassen wird, wird `mapexpr` standardmäßig auf [`identity`](@ref) gesetzt.

Verwenden Sie [`Base.include`](@ref), um eine Datei in ein anderes Modul auszuwerten.

!!! compat "Julia 1.5"
    Julia 1.5 ist erforderlich, um das Argument `mapexpr` zu übergeben.

