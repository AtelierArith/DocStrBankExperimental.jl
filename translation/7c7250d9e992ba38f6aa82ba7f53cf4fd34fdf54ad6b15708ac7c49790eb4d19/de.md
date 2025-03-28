```
open_exclusive(path::String; mode, poll_interval, wait, stale_age, refresh) :: File
```

Erstellt eine neue Datei für Lese-Schreib-Beratungs-exklusive Zugriffe. Wenn `wait` `false` ist, wird ein Fehler ausgegeben, wenn die Sperrdateien existieren, andernfalls wird blockiert, bis wir die Sperre erhalten.

Für eine Beschreibung der Schlüsselwortargumente siehe [`mkpidlock`](@ref).
