```
abspath(pfad::AbstractString, pfade::AbstractString...) -> String
```

Konvertiert eine Menge von Pfaden in einen absoluten Pfad, indem sie zusammengefügt werden und das aktuelle Verzeichnis hinzugefügt wird, falls erforderlich. Entspricht `abspath(joinpath(pfad, pfade...))`.
