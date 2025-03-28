```
hseqr!(job, compz, ilo, ihi, H, Z) -> (H, Z, w)
```

Calcula todos los valores propios y (opcionalmente) la factorización de Schur de una matriz reducida a forma de Hessenberg. Si `H` está balanceada con `gebal!`, entonces `ilo` e `ihi` son las salidas de `gebal!`. De lo contrario, deberían ser `ilo = 1` y `ihi = size(H,2)`. `tau` contiene los reflectores elementales de la factorización.
