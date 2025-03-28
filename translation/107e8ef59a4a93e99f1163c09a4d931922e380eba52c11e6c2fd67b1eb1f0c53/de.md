```
pkgversion(m::Module)
```

Gibt die Version des Pakets zurück, das das Modul `m` importiert hat, oder `nothing`, wenn `m` nicht aus einem Paket importiert wurde oder aus einem Paket ohne festgelegtes Versionsfeld importiert wurde.

Die Version wird während des Paketladens aus der Project.toml des Pakets gelesen.

Um die Version des Pakets zu erhalten, das das aktuelle Modul importiert hat, kann die Form `pkgversion(@__MODULE__)` verwendet werden.

!!! compat "Julia 1.9"
    Diese Funktion wurde in Julia 1.9 eingeführt.

