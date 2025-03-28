```
@nany N expr
```

Vérifiez si l'une des expressions générées par l'expression de fonction anonyme `expr` évalue à `true`.

`@nany 3 d->(i_d > 1)` générerait l'expression `(i_1 > 1 || i_2 > 1 || i_3 > 1)`.
