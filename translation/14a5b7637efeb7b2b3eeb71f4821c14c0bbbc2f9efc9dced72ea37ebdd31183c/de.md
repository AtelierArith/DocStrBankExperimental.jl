```
touch(path::AbstractString)
touch(fd::File)
```

Aktualisiert den Zeitstempel der letzten Änderung einer Datei auf die aktuelle Zeit.

Wenn die Datei nicht existiert, wird eine neue Datei erstellt.

Gibt `path` zurück.

# Beispiele

```julia-repl
julia> write("my_little_file", 2);

julia> mtime("my_little_file")
1.5273815391135583e9

julia> touch("my_little_file");

julia> mtime("my_little_file")
1.527381559163435e9
```

Wir können sehen, dass [`mtime`](@ref) durch `touch` geändert wurde.
