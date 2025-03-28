```
@nall N expr
```

Überprüfen Sie, ob alle von dem anonymen Funktionsausdruck `expr` generierten Ausdrücke zu `true` ausgewertet werden.

`@nall 3 d->(i_d > 1)` würde den Ausdruck `(i_1 > 1 && i_2 > 1 && i_3 > 1)` generieren. Dies kann für die Überprüfung von Grenzen nützlich sein.
