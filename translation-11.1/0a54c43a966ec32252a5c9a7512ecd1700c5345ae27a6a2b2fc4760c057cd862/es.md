```
syevd!(jobz, uplo, A)
```

Encuentra los valores propios (`jobz = N`) o los valores propios y vectores propios (`jobz = V`) de una matriz simétrica `A`. Si `uplo = U`, se utiliza el triángulo superior de `A`. Si `uplo = L`, se utiliza el triángulo inferior de `A`.

Utiliza el método de dividir y conquistar, en lugar de la iteración QR utilizada por `syev!` o múltiples representaciones relativamente robustas utilizadas por `syevr!`. Consulte a James W. Demmel et al, SIAM J. Sci. Comput. 30, 3, 1508 (2008) para una comparación de la precisión y el rendimiento de diferentes métodos.
