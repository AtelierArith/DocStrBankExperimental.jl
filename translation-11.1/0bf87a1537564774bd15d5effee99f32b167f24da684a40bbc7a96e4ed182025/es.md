```
localindices(S::SharedArray)
```

Devuelve un rango que describe los "índices" predeterminados que debe manejar el proceso actual. Este rango debe interpretarse en el sentido de indexación lineal, es decir, como un sub-rango de `1:length(S)`. En contextos de múltiples procesos, devuelve un rango vacío en el proceso padre (o en cualquier proceso para el cual [`indexpids`](@ref) devuelve 0).

Vale la pena enfatizar que `localindices` existe puramente como una conveniencia, y puedes dividir el trabajo en el arreglo entre los trabajadores de la manera que desees. Para un `SharedArray`, todos los índices deberían ser igualmente rápidos para cada proceso trabajador.
