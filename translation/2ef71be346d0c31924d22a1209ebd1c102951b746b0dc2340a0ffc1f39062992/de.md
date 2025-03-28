```
realpath(path::AbstractString) -> String
```

Kanonisiert einen Pfad, indem symbolische Links aufgelöst und "." und ".." Einträge entfernt werden. Auf dateisystemen, die die Groß- und Kleinschreibung nicht unterscheiden und die Groß- und Kleinschreibung beibehalten (typischerweise Mac und Windows), wird die im Dateisystem gespeicherte Groß- und Kleinschreibung für den Pfad zurückgegeben.

(Diese Funktion wirft eine Ausnahme, wenn `path` im Dateisystem nicht existiert.)
