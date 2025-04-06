```
gees!(jobvs, A) -> (A, vs, w)
```

Calcula los valores propios (`jobvs = N`) o los valores propios y los vectores de Schur (`jobvs = V`) de la matriz `A`. `A` se sobrescribe con su forma de Schur.

Devuelve `A`, `vs` que contiene los vectores de Schur, y `w`, que contiene los valores propios.
