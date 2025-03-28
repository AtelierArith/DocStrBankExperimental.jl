```
chmod(path::AbstractString, mode::Integer; recursive::Bool=false)
```

Ändern Sie den Berechtigungsmodus von `path` auf `mode`. Nur ganzzahlige `mode`s (z. B. `0o777`) werden derzeit unterstützt. Wenn `recursive=true` und der Pfad ein Verzeichnis ist, werden alle Berechtigungen in diesem Verzeichnis rekursiv geändert. Geben Sie `path` zurück.

!!! Hinweis     Vor Julia 1.6 konnte dies die Dateisystem-ACLs unter Windows nicht korrekt manipulieren, daher wurden nur schreibgeschützte Bits für Dateien gesetzt. Es kann jetzt ACLs manipulieren.
