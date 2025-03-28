```
GC.gc([full=true])
```

Führen Sie die Speicherbereinigung durch. Das Argument `full` bestimmt die Art der Sammlung: Eine vollständige Sammlung (Standard) durchläuft alle lebenden Objekte (d.h. vollständige Markierung) und sollte Speicher von allen unerreichbaren Objekten zurückgewinnen. Eine inkrementelle Sammlung gewinnt nur Speicher von jungen Objekten zurück, die nicht erreichbar sind.

Der GC kann entscheiden, eine vollständige Sammlung durchzuführen, selbst wenn eine inkrementelle Sammlung angefordert wurde.

!!! warning
    Übermäßiger Gebrauch wird wahrscheinlich zu schlechter Leistung führen.

