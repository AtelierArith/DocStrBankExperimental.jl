```
gelsd!(A, B, rcond) -> (B, rnk)
```

Calcula la solución de menor norma de `A * X = B` encontrando la factorización `SVD` de `A`, luego dividiendo y conquistando el problema. `B` se sobrescribe con la solución `X`. Los valores singulares por debajo de `rcond` se tratarán como cero. Devuelve la solución en `B` y el rango efectivo de `A` en `rnk`.
