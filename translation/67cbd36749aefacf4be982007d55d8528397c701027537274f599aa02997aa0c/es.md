```
CompoundPeriod
```

Un `CompoundPeriod` es útil para expresar períodos de tiempo que no son un múltiplo fijo de períodos más pequeños. Por ejemplo, "un año y un día" no es un número fijo de días, pero se puede expresar utilizando un `CompoundPeriod`. De hecho, un `CompoundPeriod` se genera automáticamente mediante la adición de diferentes tipos de períodos, por ejemplo, `Year(1) + Day(1)` produce un resultado de `CompoundPeriod`.
