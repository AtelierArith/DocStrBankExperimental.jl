```
poll_file(path::AbstractString, interval_s::Real=5.007, timeout_s::Real=-1) -> (previous::StatStruct, current)
```

Überwachen Sie eine Datei auf Änderungen, indem Sie alle `interval_s` Sekunden abfragen, bis eine Änderung auftritt oder `timeout_s` Sekunden vergangen sind. Der `interval_s` sollte eine lange Periode sein; der Standardwert beträgt 5,007 Sekunden.

Gibt ein Paar von Statusobjekten `(previous, current)` zurück, wenn eine Änderung erkannt wird. Der `previous` Status ist immer ein `StatStruct`, kann jedoch alle Felder auf null gesetzt haben (was darauf hinweist, dass die Datei zuvor nicht existierte oder nicht zugänglich war).

Das `current` Statusobjekt kann ein `StatStruct`, ein `EOFError` (was darauf hinweist, dass die Zeitüberschreitung abgelaufen ist) oder eine andere Unterklasse von `Exception` sein (wenn der `stat`-Vorgang fehlgeschlagen ist - zum Beispiel, wenn der Pfad nicht existiert).

Um festzustellen, wann eine Datei geändert wurde, vergleichen Sie `current isa StatStruct && mtime(prev) != mtime(current)`, um eine Benachrichtigung über Änderungen zu erkennen. Es wird jedoch empfohlen, [`watch_file`](@ref) für diesen Vorgang zu verwenden, da es zuverlässiger und effizienter ist, obwohl es in einigen Situationen möglicherweise nicht verfügbar ist.
