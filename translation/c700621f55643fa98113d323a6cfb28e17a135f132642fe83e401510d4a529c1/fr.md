```
ExponentialBackOff(; n=1, first_delay=0.05, max_delay=10.0, factor=5.0, jitter=0.1)
```

Un itérateur [`Float64`](@ref) de longueur `n` dont les éléments augmentent exponentiellement à un rythme dans l'intervalle `factor` * (1 ± `jitter`). Le premier élément est `first_delay` et tous les éléments sont limités à `max_delay`.
