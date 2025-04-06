```
relpath(path::AbstractString, startpath::AbstractString = ".") -> String
```

Gibt einen relativen Dateipfad zu `path` entweder vom aktuellen Verzeichnis oder von einem optionalen Startverzeichnis zurück. Dies ist eine Pfadberechnung: Das Dateisystem wird nicht aufgerufen, um die Existenz oder Art von `path` oder `startpath` zu bestätigen.

Unter Windows wird die Groß- und Kleinschreibung auf jeden Teil des Pfades angewendet, mit Ausnahme der Laufwerksbuchstaben. Wenn `path` und `startpath` auf unterschiedliche Laufwerke verweisen, wird der absolute Pfad von `path` zurückgegeben.
