```
gglse!(A, c, B, d) -> (X,res)
```

Löst die Gleichung `A * x = c`, wobei `x` der Gleichheitsbedingung `B * x = d` unterliegt. Verwendet die Formel `||c - A*x||^2 = 0`, um zu lösen. Gibt `X` und die Residualsumme der Quadrate zurück.
