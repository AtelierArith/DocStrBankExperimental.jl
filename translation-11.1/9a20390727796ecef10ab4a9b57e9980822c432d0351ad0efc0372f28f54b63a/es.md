```
Random.default_rng() -> rng
```

Devuelve el generador de números aleatorios (RNG) global predeterminado, que es utilizado por las funciones relacionadas con `rand` cuando no se proporciona un RNG explícito.

Cuando se carga el módulo `Random`, el RNG predeterminado se inicializa *aleatoriamente*, a través de [`Random.seed!()`](@ref): esto significa que cada vez que se inicia una nueva sesión de julia, la primera llamada a `rand()` produce un resultado diferente, a menos que se llame primero a `seed!(seed)`.

Es seguro para hilos: hilos distintos pueden llamar de manera segura a funciones relacionadas con `rand` en `default_rng()` de forma concurrente, por ejemplo, `rand(default_rng())`.

!!! nota
    El tipo del RNG predeterminado es un detalle de implementación. A través de diferentes versiones de Julia, no deberías esperar que el RNG predeterminado siempre tenga el mismo tipo, ni que produzca la misma secuencia de números aleatorios para una semilla dada.


!!! compat "Julia 1.3"
    Esta función fue introducida en Julia 1.3.

