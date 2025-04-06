```
eachline(io::IO=stdin; keep::Bool=false)
eachline(filename::AbstractString; keep::Bool=false)
```

Erstellen Sie ein iterierbares `EachLine`-Objekt, das jede Zeile aus einem I/O-Stream oder einer Datei liefert. Die Iteration ruft wiederholt [`readline`](@ref) mit dem Stream-Argument auf, wobei `keep` übergeben wird, um zu bestimmen, ob nachfolgende Zeilenendezeichen beibehalten werden. Wenn mit einem Dateinamen aufgerufen, wird die Datei zu Beginn der Iteration einmal geöffnet und am Ende geschlossen. Wenn die Iteration unterbrochen wird, wird die Datei geschlossen, wenn das `EachLine`-Objekt garbage collected wird.

Um über jede Zeile eines `String` zu iterieren, kann `eachline(IOBuffer(str))` verwendet werden.

[`Iterators.reverse`](@ref) kann auf ein `EachLine`-Objekt angewendet werden, um die Zeilen in umgekehrter Reihenfolge zu lesen (für Dateien, Puffer und andere I/O-Streams, die [`seek`](@ref) unterstützen), und [`first`](@ref) oder [`last`](@ref) können verwendet werden, um die ersten oder letzten Zeilen zu extrahieren.

# Beispiele

```jldoctest
julia> write("my_file.txt", "JuliaLang ist eine GitHub-Organisation.\n Es hat viele Mitglieder.\n");

julia> for line in eachline("my_file.txt")
           print(line)
       end
JuliaLang ist eine GitHub-Organisation. Es hat viele Mitglieder.

julia> rm("my_file.txt");
```

!!! compat "Julia 1.8"
    Julia 1.8 ist erforderlich, um `Iterators.reverse` oder `last` mit `eachline`-Iteratoren zu verwenden.

