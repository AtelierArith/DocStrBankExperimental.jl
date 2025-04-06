```
similar(storagetype, axes)
```

Erstellt ein uninitialisiertes veränderliches Array, das dem durch `storagetype` angegebenen entspricht, jedoch mit `axes`, die durch das letzte Argument angegeben sind.

**Beispiele**:

```
similar(Array{Int}, axes(A))
```

erstellt ein Array, das "wie" ein `Array{Int}` funktioniert (und möglicherweise tatsächlich von einem unterstützt wird), aber das identisch zu `A` indiziert wird. Wenn `A` eine konventionelle Indizierung hat, ist dies identisch zu `Array{Int}(undef, size(A))`, aber wenn `A` eine unkonventionelle Indizierung hat, dann stimmen die Indizes des Ergebnisses mit denen von `A` überein.

```
similar(BitArray, (axes(A, 2),))
```

würde ein eindimensionales logisches Array erstellen, dessen Indizes mit denen der Spalten von `A` übereinstimmen. ```
