```
mkpath(path::AbstractString; mode::Unsigned = 0o777)
```

Erstellt alle erforderlichen Zwischenverzeichnisse im `path`. Verzeichnisse werden mit den Berechtigungen `mode` erstellt, die standardmäßig auf `0o777` gesetzt sind und durch die aktuelle Dateierstellungsmaske modifiziert werden. Im Gegensatz zu [`mkdir`](@ref) gibt es bei `mkpath` keinen Fehler, wenn `path` (oder Teile davon) bereits existiert. Ein Fehler wird jedoch ausgelöst, wenn `path` (oder Teile davon) auf eine vorhandene Datei verweist. Gibt `path` zurück.

Wenn `path` einen Dateinamen enthält, möchten Sie wahrscheinlich `mkpath(dirname(path))` verwenden, um zu vermeiden, dass ein Verzeichnis mit dem Dateinamen erstellt wird.

# Beispiele

```julia-repl
julia> cd(mktempdir())

julia> mkpath("my/test/dir") # erstellt drei Verzeichnisse
"my/test/dir"

julia> readdir()
1-element Array{String,1}:
 "my"

julia> cd("my")

julia> readdir()
1-element Array{String,1}:
 "test"

julia> readdir("test")
1-element Array{String,1}:
 "dir"

julia> mkpath("intermediate_dir/actually_a_directory.txt") # erstellt zwei Verzeichnisse
"intermediate_dir/actually_a_directory.txt"

julia> isdir("intermediate_dir/actually_a_directory.txt")
true

```
