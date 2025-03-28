```
circshift!(dest, src, shifts)
```

Zirkulär verschieben, d.h. die Daten in `src` rotieren und das Ergebnis in `dest` speichern. `shifts` gibt die Menge an, um die in jeder Dimension verschoben werden soll.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein veränderter Parameter Speicher mit einem anderen Parameter teilt.


Siehe auch [`circshift`](@ref).
