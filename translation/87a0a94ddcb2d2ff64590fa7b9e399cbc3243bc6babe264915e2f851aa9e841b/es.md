```
gttrf!(dl, d, du) -> (dl, d, du, du2, ipiv)
```

Encuentra la factorización `LU` de una matriz tridiagonal con `dl` en la subdiagonal, `d` en la diagonal y `du` en la superdiagonal.

Modifica `dl`, `d` y `du` en su lugar y devuelve estos junto con la segunda superdiagonal `du2` y el vector de pivoteo `ipiv`.
