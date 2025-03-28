```
@nall N expr
```

Vérifiez si toutes les expressions générées par l'expression de fonction anonyme `expr` évaluent à `true`.

`@nall 3 d->(i_d > 1)` générerait l'expression `(i_1 > 1 && i_2 > 1 && i_3 > 1)`. Cela peut être pratique pour vérifier les limites.
