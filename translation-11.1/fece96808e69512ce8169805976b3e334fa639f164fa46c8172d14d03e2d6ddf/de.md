```
ParserError
```

Der Typ, der von [`tryparse`](@ref) und [`tryparsefile`](@ref) zurückgegeben wird, wenn das Parsen fehlschlägt. Er enthält (unter anderem) die folgenden Felder:

  * `pos`, die Position im String, an der der Fehler aufgetreten ist
  * `table`, das Ergebnis, das bisher erfolgreich geparst wurde
  * `type`, ein Fehlertyp, der für verschiedene Arten von Fehlern unterschiedlich ist
