```
disable_logging(level)
```

Deaktiviert alle Protokollnachrichten auf Protokollebene, die gleich oder niedriger als `level` sind. Dies ist eine *globale* Einstellung, die dazu gedacht ist, das Debug-Protokollieren extrem kostengünstig zu machen, wenn es deaktiviert ist.

# Beispiele

```julia
Logging.disable_logging(Logging.Info) # Deaktiviert Debug- und Informationsprotokolle
```
