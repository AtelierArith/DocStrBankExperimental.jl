```
ExponentialBackOff(; n=1, first_delay=0.05, max_delay=10.0, factor=5.0, jitter=0.1)
```

Un iterador de [`Float64`](@ref) de longitud `n` cuyos elementos aumentan exponencialmente a una tasa en el intervalo `factor` * (1 ± `jitter`). El primer elemento es `first_delay` y todos los elementos están limitados a `max_delay`.
