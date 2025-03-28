```
@nany N expr
```

Verifica si alguna de las expresiones generadas por la expresión de función anónima `expr` evalúa a `true`.

`@nany 3 d->(i_d > 1)` generaría la expresión `(i_1 > 1 || i_2 > 1 || i_3 > 1)`.
