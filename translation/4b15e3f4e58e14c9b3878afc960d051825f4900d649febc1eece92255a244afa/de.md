```
@nany N expr
```

Überprüfen Sie, ob eine der durch den anonymen Funktionsausdruck `expr` generierten Ausdrücke `true` ergibt.

`@nany 3 d->(i_d > 1)` würde den Ausdruck `(i_1 > 1 || i_2 > 1 || i_3 > 1)` generieren.
