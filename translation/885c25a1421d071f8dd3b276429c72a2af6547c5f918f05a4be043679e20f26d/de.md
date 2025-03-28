```
normpath(pfad::AbstractString, pfade::AbstractString...) -> String
```

Konvertiert eine Menge von Pfaden in einen normalisierten Pfad, indem sie zusammengefügt und "." und ".." Einträge entfernt werden. Entspricht `normpath(joinpath(pfad, pfade...))`.
