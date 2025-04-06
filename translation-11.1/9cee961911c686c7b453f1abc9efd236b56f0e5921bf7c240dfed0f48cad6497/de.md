```
eigen!(A; permute, scale, sortby)
eigen!(A, B; sortby)
```

Dasselbe wie [`eigen`](@ref), aber spart Speicherplatz, indem es die Eingabe `A` (und `B`) überschreibt, anstatt eine Kopie zu erstellen.
