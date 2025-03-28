```
Base.checked_neg(x)
```

Calcula `-x`, verificando errores de desbordamiento donde sea aplicable. Por ejemplo, los enteros con signo de complemento a dos estándar (por ejemplo, `Int`) no pueden representar `-typemin(Int)`, lo que lleva a un desbordamiento.

La protección contra desbordamiento puede imponer una penalización de rendimiento perceptible.
