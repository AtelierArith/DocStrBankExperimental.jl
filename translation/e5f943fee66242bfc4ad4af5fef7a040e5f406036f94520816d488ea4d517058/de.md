```
abspath(path::AbstractString) -> String
```

Konvertiert einen Pfad in einen absoluten Pfad, indem das aktuelle Verzeichnis hinzugefügt wird, falls erforderlich. Normalisiert auch den Pfad wie in [`normpath`](@ref).

# Beispiele

Wenn Sie sich in einem Verzeichnis namens `JuliaExample` befinden und die Daten, die Sie verwenden, zwei Ebenen über dem Verzeichnis `JuliaExample` liegen, könnten Sie schreiben:

```
abspath("../../data")
```

Was einen Pfad wie `"/home/JuliaUser/data/"` ergibt.

Siehe auch [`joinpath`](@ref), [`pwd`](@ref), [`expanduser`](@ref).
