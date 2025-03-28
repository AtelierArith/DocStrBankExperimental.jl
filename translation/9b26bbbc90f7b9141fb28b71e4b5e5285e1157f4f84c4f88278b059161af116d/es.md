```
geqrt!(A, nb) -> (A, T)
```

Calcula la factorización `QR` bloqueada de `A`, `A = QR`. `nb` establece el tamaño del bloque y debe estar entre 1 y `n`, la segunda dimensión de `A`.

Devuelve `A`, modificado en su lugar, y `T`, que contiene reflectores de bloque triangulares superiores que parametrizan los reflectores elementales de la factorización.
