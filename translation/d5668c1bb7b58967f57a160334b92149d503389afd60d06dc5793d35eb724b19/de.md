```
chown(path::AbstractString, owner::Integer, group::Integer=-1)
```

Ändert den Besitzer und/oder die Gruppe von `path` in `owner` und/oder `group`. Wenn der eingegebene Wert für `owner` oder `group` `-1` ist, wird die entsprechende ID nicht geändert. Derzeit werden nur ganze Zahlen für `owner` und `group` unterstützt. Gibt `path` zurück.
