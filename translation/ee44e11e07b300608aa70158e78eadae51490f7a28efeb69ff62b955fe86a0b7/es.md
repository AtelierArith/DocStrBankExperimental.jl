```
precision(num::AbstractFloat; base::Integer=2)
precision(T::Type; base::Integer=2)
```

Obtiene la precisión de un número de punto flotante, tal como se define por el número efectivo de bits en el significante, o la precisión de un tipo de punto flotante `T` (su valor predeterminado actual, si `T` es un tipo de precisión variable como [`BigFloat`](@ref)).

Si se especifica `base`, entonces devuelve el número máximo correspondiente de dígitos del significante en esa base.

!!! compat "Julia 1.8"
    La palabra clave `base` requiere al menos Julia 1.8.

