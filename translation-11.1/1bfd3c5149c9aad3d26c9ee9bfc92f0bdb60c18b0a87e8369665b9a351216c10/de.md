```
GC.enable(on::Bool)
```

Steuern, ob die Speicherbereinigung aktiviert ist, indem ein boolesches Argument verwendet wird (`true` für aktiviert, `false` für deaktiviert). Gibt den vorherigen Zustand der Speicherbereinigung zurück.

!!! warning
    Das Deaktivieren der Speicherbereinigung sollte nur mit Vorsicht verwendet werden, da es dazu führen kann, dass der Speicherverbrauch unbegrenzt ansteigt.

