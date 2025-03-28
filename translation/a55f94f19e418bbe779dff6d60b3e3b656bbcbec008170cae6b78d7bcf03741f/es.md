```
eval(expr)
```

Evalúa una expresión en el ámbito global del módulo que la contiene. Cada `Module` (excepto aquellos definidos con `baremodule`) tiene su propia definición de `eval` con un argumento, que evalúa expresiones en ese módulo.
