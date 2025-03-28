```
stebz!(rango, orden, vl, vu, il, iu, abstol, dv, ev) -> (dv, iblock, isplit)
```

Calcula los valores propios para una matriz tridiagonal simétrica con `dv` como diagonal y `ev` como off-diagonal. Si `rango = A`, se encuentran todos los valores propios. Si `rango = V`, se encuentran los valores propios en el intervalo semiabierto `(vl, vu]`. Si `rango = I`, se encuentran los valores propios con índices entre `il` y `iu`. Si `orden = B`, los valores propios se ordenan dentro de un bloque. Si `orden = E`, se ordenan a través de todos los bloques. `abstol` se puede establecer como una tolerancia para la convergencia.
