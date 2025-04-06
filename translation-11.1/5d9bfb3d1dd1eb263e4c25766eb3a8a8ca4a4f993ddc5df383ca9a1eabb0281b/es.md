```
stegr!(jobz, range, dv, ev, vl, vu, il, iu) -> (w, Z)
```

Calcula los valores propios (`jobz = N`) o los valores propios y vectores propios (`jobz = V`) para una matriz tridiagonal simétrica con `dv` como diagonal y `ev` como subdiagonal. Si `range = A`, se encuentran todos los valores propios. Si `range = V`, se encuentran los valores propios en el intervalo semiabierto `(vl, vu]`. Si `range = I`, se encuentran los valores propios con índices entre `il` y `iu`. Los valores propios se devuelven en `w` y los vectores propios en `Z`.
