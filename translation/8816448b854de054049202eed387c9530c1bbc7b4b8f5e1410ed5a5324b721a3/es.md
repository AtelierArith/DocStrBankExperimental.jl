```
randjump(r::MersenneTwister, steps::Integer) -> MersenneTwister
```

Crea un objeto `MersenneTwister` inicializado, cuyo estado se mueve hacia adelante (sin generar números) desde `r` por `steps` pasos. Un paso de este tipo corresponde a la generación de dos números `Float64`. Para cada valor diferente de `steps`, se debe generar internamente un gran polinomio. Uno ya está precomputado para `steps=big(10)^20`.
