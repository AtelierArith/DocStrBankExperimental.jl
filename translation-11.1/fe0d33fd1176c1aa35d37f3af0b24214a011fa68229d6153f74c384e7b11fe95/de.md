```
Base.compilecache(module::PkgId)
```

Erstellt eine vorcompilierte Cache-Datei für ein Modul und alle seine Abhängigkeiten. Dies kann verwendet werden, um die Ladezeiten von Paketen zu reduzieren. Cache-Dateien werden in `DEPOT_PATH[1]/compiled` gespeichert. Siehe [Modulinitialisierung und Vorcompilierung](@ref) für wichtige Hinweise.
