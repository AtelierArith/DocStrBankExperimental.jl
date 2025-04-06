```
mkfifo(path::AbstractString, [mode::Integer]) -> path
```

Erstellt eine FIFO-Sonderdatei (eine benannte Pipe) unter `path`. Gibt `path` im Erfolgsfall unverändert zurück.

`mkfifo` wird nur auf Unix-Plattformen unterstützt.

!!! compat "Julia 1.11"
    `mkfifo` erfordert mindestens Julia 1.11.

