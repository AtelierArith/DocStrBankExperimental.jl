```
displaysize([io::IO]) -> (lines, columns)
```

Gibt die nominale Größe des Bildschirms zurück, die für die Ausgabe an dieses `IO`-Objekt verwendet werden kann. Wenn keine Eingabe bereitgestellt wird, werden die Umgebungsvariablen `LINES` und `COLUMNS` gelesen. Wenn diese nicht gesetzt sind, wird eine Standardgröße von `(24, 80)` zurückgegeben.

# Beispiele

```jldoctest
julia> withenv("LINES" => 30, "COLUMNS" => 100) do
           displaysize()
       end
(30, 100)
```

Um die Größe Ihres TTY zu erhalten,

```julia-repl
julia> displaysize(stdout)
(34, 147)
```
