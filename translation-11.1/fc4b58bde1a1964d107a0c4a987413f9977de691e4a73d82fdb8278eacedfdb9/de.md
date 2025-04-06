```
ZeroPivotException <: Exception
```

Ausnahme, die ausgelöst wird, wenn eine Matrixfaktorisierung/-lösung auf eine Null in einer Pivot- (diagonal) Position stößt und nicht fortfahren kann. Dies bedeutet *nicht* unbedingt, dass die Matrix singulär ist: Es kann sinnvoll sein, zu einer anderen Faktorisierung wie pivotiertem LU zu wechseln, die Variablen neu anordnen kann, um spurious Null-Pivots zu eliminieren. Das Feld `info` gibt den Standort (einen der) Null-Pivots an.
