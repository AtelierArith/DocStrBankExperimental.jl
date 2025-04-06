```
init(; n::Integer, delay::Real)
```

Konfigurieren Sie die `delay` zwischen Rückverfolgungen (gemessen in Sekunden) und die Anzahl `n` der Befehlszeiger, die pro Thread gespeichert werden können. Jeder Befehlszeiger entspricht einer einzelnen Codezeile; Rückverfolgungen bestehen im Allgemeinen aus einer langen Liste von Befehlszeigern. Beachten Sie, dass 6 Plätze für Befehlszeiger pro Rückverfolgung verwendet werden, um Metadaten und zwei NULL-Endmarkierungen zu speichern. Die aktuellen Einstellungen können abgerufen werden, indem Sie diese Funktion ohne Argumente aufrufen, und jede kann unabhängig mit Schlüsselwörtern oder in der Reihenfolge `(n, delay)` festgelegt werden.
