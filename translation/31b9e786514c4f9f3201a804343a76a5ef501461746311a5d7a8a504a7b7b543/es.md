```
@nall N expr
```

Verifica si todas las expresiones generadas por la expresión de función anónima `expr` se evalúan como `true`.

`@nall 3 d->(i_d > 1)` generaría la expresión `(i_1 > 1 && i_2 > 1 && i_3 > 1)`. Esto puede ser conveniente para la verificación de límites.
