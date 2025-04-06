```
gglse!(A, c, B, d) -> (X,res)
```

Resuelve la ecuación `A * x = c` donde `x` está sujeto a la restricción de igualdad `B * x = d`. Utiliza la fórmula `||c - A*x||^2 = 0` para resolver. Devuelve `X` y la suma de cuadrados residuales.
