```
ExponentialBackOff(; n=1, first_delay=0.05, max_delay=10.0, factor=5.0, jitter=0.1)
```

Ein [`Float64`](@ref) Iterator der Länge `n`, dessen Elemente exponentiell mit einer Rate im Intervall `factor` * (1 ± `jitter`) zunehmen. Das erste Element ist `first_delay` und alle Elemente sind auf `max_delay` begrenzt.
