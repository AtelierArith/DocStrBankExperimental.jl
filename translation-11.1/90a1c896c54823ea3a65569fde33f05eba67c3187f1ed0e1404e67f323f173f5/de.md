```
BitSet([itr])
```

Konstruiere eine sortierte Menge von `Int`s, die durch das gegebene iterable Objekt erzeugt wird, oder eine leere Menge. Implementiert als Bit-String und daher für dichte Ganzzahlenmengen ausgelegt. Wenn die Menge spärlich sein wird (zum Beispiel, wenn sie einige sehr große Ganzzahlen enthält), verwende stattdessen [`Set`](@ref).
