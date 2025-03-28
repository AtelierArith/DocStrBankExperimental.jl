```
tryopen_exclusive(path::String, mode::Integer = 0o444) :: Union{Void, File}
```

Versuchen Sie, eine neue Datei für den Lese-Schreib-Zugriff mit exklusiver Beratung zu erstellen. Geben Sie nichts zurück, wenn sie bereits existiert.
