```
rm(path::AbstractString; force::Bool=false, recursive::Bool=false)
```

Löschen Sie die Datei, den Link oder das leere Verzeichnis am angegebenen Pfad. Wenn `force=true` übergeben wird, wird ein nicht vorhandener Pfad nicht als Fehler behandelt. Wenn `recursive=true` übergeben wird und der Pfad ein Verzeichnis ist, werden alle Inhalte rekursiv entfernt.

# Beispiele

```jldoctest
julia> mkpath("my/test/dir");

julia> rm("my", recursive=true)

julia> rm("this_file_does_not_exist", force=true)

julia> rm("this_file_does_not_exist")
ERROR: IOError: unlink("this_file_does_not_exist"): no such file or directory (ENOENT)
Stacktrace:
[...]
```
