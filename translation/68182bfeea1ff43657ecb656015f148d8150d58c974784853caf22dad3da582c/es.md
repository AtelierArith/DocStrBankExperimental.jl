```
Sampler(rng, x, repetition = Val(Inf))
```

Devuelve un objeto sampler que se puede usar para generar valores aleatorios de `rng` para `x`.

Cuando `sp = Sampler(rng, x, repetition)`, `rand(rng, sp)` se utilizará para extraer valores aleatorios y debe definirse en consecuencia.

`repetition` puede ser `Val(1)` o `Val(Inf)`, y debe usarse como una sugerencia para decidir la cantidad de precomputación, si corresponde.

[`Random.SamplerType`](@ref) y [`Random.SamplerTrivial`](@ref) son retrocesos predeterminados para *tipos* y *valores*, respectivamente. [`Random.SamplerSimple`](@ref) se puede usar para almacenar valores precomputados sin definir tipos adicionales solo para este propósito.
