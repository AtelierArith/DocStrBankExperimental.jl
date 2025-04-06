```
gelqf!(A, tau)
```

Calcula la factorización `LQ` de `A`, `A = LQ`. `tau` contiene escalares que parametrizan los reflectores elementales de la factorización. `tau` debe tener una longitud mayor o igual a la dimensión más pequeña de `A`.

Devuelve `A` y `tau` modificados en su lugar.
