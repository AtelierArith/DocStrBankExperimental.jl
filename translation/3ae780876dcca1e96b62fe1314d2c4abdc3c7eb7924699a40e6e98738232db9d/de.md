```
with(f::Function, obj)
```

Hilfsfunktion für das Ressourcenmanagement. Wendet `f` auf `obj` an und stellt sicher, dass `close` auf `obj` aufgerufen wird, nachdem `f` erfolgreich zurückgegeben hat oder einen Fehler ausgelöst hat. Stellt sicher, dass zugewiesene Git-Ressourcen so schnell wie möglich finalisiert werden, sobald sie nicht mehr benötigt werden.
