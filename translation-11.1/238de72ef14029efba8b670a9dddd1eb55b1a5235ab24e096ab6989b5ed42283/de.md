```
mkdir(path::AbstractString; mode::Unsigned = 0o777)
```

Erstellen Sie ein neues Verzeichnis mit dem Namen `path` und den Berechtigungen `mode`. `mode` hat standardmäßig den Wert `0o777`, der durch die aktuelle Dateierstellungsmaske modifiziert wird. Diese Funktion erstellt niemals mehr als ein Verzeichnis. Wenn das Verzeichnis bereits existiert oder einige Zwischenverzeichnisse nicht existieren, wirft diese Funktion einen Fehler. Siehe [`mkpath`](@ref) für eine Funktion, die alle erforderlichen Zwischenverzeichnisse erstellt. Gibt `path` zurück.

# Beispiele

```julia-repl
julia> mkdir("testingdir")
"testingdir"

julia> cd("testingdir")

julia> pwd()
"/home/JuliaUser/testingdir"
```
