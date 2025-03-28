```
deserialize(stream)
```

Liest einen Wert, der von [`serialize`](@ref) geschrieben wurde. `deserialize` geht davon aus, dass die binären Daten, die aus `stream` gelesen werden, korrekt sind und von einer kompatiblen Implementierung von [`serialize`](@ref) serialisiert wurden. `deserialize` ist für Einfachheit und Leistung konzipiert und validiert daher die gelesenen Daten nicht. Fehlformatierte Daten können zu einem Prozessabbruch führen. Der Aufrufer muss die Integrität und Richtigkeit der aus `stream` gelesenen Daten sicherstellen.
