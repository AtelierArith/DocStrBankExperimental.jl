```
gges!(jobvsl, jobvsr, A, B) -> (A, B, alpha, beta, vsl, vsr)
```

Calcula los valores propios generalizados, la forma de Schur generalizada, los vectores de Schur izquierdos (`jobsvl = V`), o los vectores de Schur derechos (`jobvsr = V`) de `A` y `B`.

Los valores propios generalizados se devuelven en `alpha` y `beta`. Los vectores de Schur izquierdos se devuelven en `vsl` y los vectores de Schur derechos se devuelven en `vsr`.
