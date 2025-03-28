```
syevr!(jobz, range, uplo, A, vl, vu, il, iu, abstol) -> (W, Z)
```

Encuentra los valores propios (`jobz = N`) o los valores propios y vectores propios (`jobz = V`) de una matriz simétrica `A`. Si `uplo = U`, se utiliza el triángulo superior de `A`. Si `uplo = L`, se utiliza el triángulo inferior de `A`. Si `range = A`, se encuentran todos los valores propios. Si `range = V`, se encuentran los valores propios en el intervalo semiabierto `(vl, vu]`. Si `range = I`, se encuentran los valores propios con índices entre `il` y `iu`. `abstol` se puede establecer como una tolerancia para la convergencia.

Los valores propios se devuelven en `W` y los vectores propios en `Z`.
