```
pick(m::AbstractMenu, cursor::Int)
```

Definiert, was passiert, wenn ein Benutzer die Eingabetaste drückt, während das Menü geöffnet ist. Wenn `true` zurückgegeben wird, wird `request()` beendet. `cursor` indiziert die Position der Auswahl.
