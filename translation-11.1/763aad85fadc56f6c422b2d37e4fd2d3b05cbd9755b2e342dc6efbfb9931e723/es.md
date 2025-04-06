```
bdsdc!(uplo, compq, d, e_) -> (d, e, u, vt, q, iq)
```

Calcula la descomposición en valores singulares de una matriz bidiagonal con `d` en la diagonal y `e_` en la subdiagonal utilizando un método de dividir y conquistar. Si `uplo = U`, `e_` es la superdiagonal. Si `uplo = L`, `e_` es la subdiagonal. Si `compq = N`, solo se encuentran los valores singulares. Si `compq = I`, se encuentran los valores y vectores singulares. Si `compq = P`, se encuentran los valores y vectores singulares en forma compacta. Solo funciona para tipos reales.

Devuelve los valores singulares en `d`, y si `compq = P`, los vectores singulares compactos en `iq`.
