Der `Header`-Typ ist eine Struktur, die die wesentlichen Metadaten für einen einzelnen Datensatz in einer Tar-Datei mit dieser Definition darstellt:

```
struct Header
    path :: String # Pfad relativ zum Root
    type :: Symbol # Typindikator (siehe unten)
    mode :: UInt16 # Modus/Berechtigungen (am besten in oktal anzeigen)
    size :: Int64  # Größe der Datensatzdaten in Bytes
    link :: String # Zielpfad eines Symlinks
end
```

Typen werden mit den folgenden Symbolen dargestellt: `file`, `hardlink`, `symlink`, `chardev`, `blockdev`, `directory`, `fifo` oder für unbekannte Typen das Typflag-Zeichen als Symbol. Beachten Sie, dass [`extract`](@ref) sich weigert, Datensätze anderer Typen als `file`, `symlink` und `directory` zu extrahieren; [`list`](@ref) listet andere Arten von Datensätzen nur auf, wenn es mit `strict=false` aufgerufen wird.

Das Tar-Format enthält verschiedene andere Metadaten über Datensätze, einschließlich Benutzer- und Gruppen-IDs, Benutzer- und Gruppennamen sowie Zeitstempel. Das `Tar`-Paket ignoriert diese absichtlich vollständig. Beim Erstellen von Tar-Dateien werden diese Felder immer auf null/leer gesetzt. Beim Lesen von Tar-Dateien werden diese Felder ignoriert, abgesehen von der Überprüfung der Header-Prüfziffern für jeden Header-Datensatz für alle Felder.
