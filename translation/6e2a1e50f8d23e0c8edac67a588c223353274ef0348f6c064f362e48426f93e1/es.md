```
Base.checked_abs(x)
```

Calcula `abs(x)`, verificando errores de desbordamiento donde sea aplicable. Por ejemplo, los enteros con signo en complemento a dos estándar (por ejemplo, `Int`) no pueden representar `abs(typemin(Int))`, lo que lleva a un desbordamiento.

La protección contra desbordamientos puede imponer una penalización de rendimiento perceptible.
