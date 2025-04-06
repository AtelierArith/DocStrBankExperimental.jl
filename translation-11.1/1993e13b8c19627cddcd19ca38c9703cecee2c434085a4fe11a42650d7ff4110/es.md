```
SamplerTrivial(x)
```

Crea un muestreador que simplemente envuelve el valor dado `x`. Este es el valor predeterminado de reserva para valores. El `eltype` de este muestreador es igual a `eltype(x)`.

El caso de uso recomendado es muestrear de valores sin datos precomputados.
