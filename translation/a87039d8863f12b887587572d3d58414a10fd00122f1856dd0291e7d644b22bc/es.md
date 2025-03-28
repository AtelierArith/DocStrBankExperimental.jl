```
SamplerSimple(x, data)
```

Crea un muestreador que envuelve el valor dado `x` y los `data`. El `eltype` de este muestreador es igual a `eltype(x)`.

El caso de uso recomendado es muestrear de valores con datos precomputados.
