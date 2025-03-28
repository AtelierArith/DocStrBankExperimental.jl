```
pointer_from_objref(x)
```

Erhalten Sie die Speicheradresse eines Julia-Objekts als `Ptr`. Die Existenz des resultierenden `Ptr` schützt das Objekt nicht vor der Garbage Collection, daher müssen Sie sicherstellen, dass das Objekt während der gesamten Zeit, in der der `Ptr` verwendet wird, referenziert bleibt.

Diese Funktion darf nicht auf unveränderlichen Objekten aufgerufen werden, da diese keine stabilen Speicheradressen haben.

Siehe auch [`unsafe_pointer_to_objref`](@ref).
