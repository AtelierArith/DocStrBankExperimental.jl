```
with_warn(f::Function, ::Type{T}, args...)
```

Ressourcenverwaltungs-Hilfsfunktion. Wendet `f` auf `args` an, indem zuerst eine Instanz des Typs `T` aus `args` erstellt wird. Stellt sicher, dass `close` auf dem resultierenden Objekt aufgerufen wird, nachdem `f` erfolgreich zurückgegeben hat oder einen Fehler auslöst. Stellt sicher, dass zugewiesene Git-Ressourcen so schnell wie möglich finalisiert werden, sobald sie nicht mehr benötigt werden. Wenn ein Fehler von `f` ausgelöst wird, wird eine Warnung angezeigt, die den Fehler enthält.
