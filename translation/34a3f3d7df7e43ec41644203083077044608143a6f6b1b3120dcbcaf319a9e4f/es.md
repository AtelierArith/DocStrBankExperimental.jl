```
geqrt!(A, T)
```

Calcula la factorización `QR` bloqueada de `A`, `A = QR`. `T` contiene reflectores de bloque triangulares superiores que parametrizan los reflectores elementales de la factorización. La primera dimensión de `T` establece el tamaño del bloque y debe estar entre 1 y `n`. La segunda dimensión de `T` debe ser igual a la dimensión más pequeña de `A`.

Devuelve `A` y `T` modificados en su lugar.
