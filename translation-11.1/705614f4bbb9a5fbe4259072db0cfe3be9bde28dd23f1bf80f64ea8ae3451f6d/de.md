```
readdlm(source, delim::AbstractChar, T::Type, eol::AbstractChar; header=false, skipstart=0, skipblanks=true, use_mmap, quotes=true, dims, comments=false, comment_char='#')
```

Liest eine Matrix aus der Quelle, wobei jede Zeile (getrennt durch `eol`) eine Reihe ergibt, mit Elementen, die durch den angegebenen Trenner getrennt sind. Die Quelle kann eine Textdatei, ein Stream oder ein Byte-Array sein. Speicher-mapped Dateien können verwendet werden, indem die Byte-Array-Darstellung des gemappten Segments als Quelle übergeben wird.

Wenn `T` ein numerischer Typ ist, ist das Ergebnis ein Array dieses Typs, wobei alle nicht-numerischen Elemente als `NaN` für Fließkommatypen oder null dargestellt werden. Andere nützliche Werte von `T` sind `String`, `AbstractString` und `Any`.

Wenn `header` auf `true` gesetzt ist, wird die erste Datenzeile als Header gelesen und das Tupel `(data_cells, header_cells)` wird anstelle von nur `data_cells` zurückgegeben.

Die Angabe von `skipstart` ignoriert die entsprechende Anzahl von Anfangszeilen aus der Eingabe.

Wenn `skipblanks` auf `true` gesetzt ist, werden leere Zeilen in der Eingabe ignoriert.

Wenn `use_mmap` auf `true` gesetzt ist, wird die durch `source` angegebene Datei für potenzielle Geschwindigkeitsvorteile im Speicher gemappt, wenn die Datei groß ist. Standard ist `false`. Auf einem Windows-Dateisystem sollte `use_mmap` nicht auf `true` gesetzt werden, es sei denn, die Datei wird nur einmal gelesen und auch nicht beschrieben. Es gibt einige Randfälle, in denen ein Betriebssystem Unix-ähnlich ist, das Dateisystem jedoch Windows-ähnlich ist.

Wenn `quotes` auf `true` gesetzt ist, dürfen Spalten, die in doppelte Anführungszeichen (") eingeschlossen sind, neue Zeilen und Spaltentrenner enthalten. Doppelte Anführungszeichen innerhalb eines zitierten Feldes müssen mit einem weiteren doppelten Anführungszeichen escaped werden. Die Angabe von `dims` als Tupel der erwarteten Zeilen und Spalten (einschließlich Header, falls vorhanden) kann das Lesen großer Dateien beschleunigen. Wenn `comments` auf `true` gesetzt ist, werden Zeilen, die mit `comment_char` beginnen, und der Text, der `comment_char` in einer Zeile folgt, ignoriert.

# Beispiele

```jldoctest
julia> using DelimitedFiles

julia> x = [1; 2; 3; 4];

julia> y = [5; 6; 7; 8];

julia> open("delim_file.txt", "w") do io
           writedlm(io, [x y])
       end

julia> readdlm("delim_file.txt", '\t', Int, '\n')
4×2 Matrix{Int64}:
 1  5
 2  6
 3  7
 4  8

julia> rm("delim_file.txt")
```
