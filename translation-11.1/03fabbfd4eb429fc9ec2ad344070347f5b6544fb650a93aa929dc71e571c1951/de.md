```
get_zero_subnormals() -> Bool
```

Gibt `false` zurück, wenn Operationen mit subnormalen Gleitkommawerten ("denormals") den Regeln der IEEE-Arithmetik folgen, und `true`, wenn sie möglicherweise in Nullen umgewandelt werden können.

!!! warning
    Diese Funktion betrifft nur den aktuellen Thread.

