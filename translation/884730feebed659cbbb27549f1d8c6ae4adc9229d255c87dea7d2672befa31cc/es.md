```
setprecision([T=BigFloat,] precision::Int; base=2)
```

Establece la precisión (en bits, por defecto) que se utilizará para la aritmética de `T`. Si se especifica `base`, entonces la precisión es la mínima requerida para dar al menos `precision` dígitos en la `base` dada.

!!! warning
    Esta función no es segura para hilos. Afectará al código que se ejecute en todos los hilos, pero su comportamiento es indefinido si se llama de manera concurrente con cálculos que utilizan la configuración.


!!! compat "Julia 1.8"
    La palabra clave `base` requiere al menos Julia 1.8.

