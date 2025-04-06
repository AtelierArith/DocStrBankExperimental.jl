```
randsubseq([rng=default_rng(),] A, p) -> Vector
```

Devuelve un vector que consiste en una subsecuencia aleatoria del arreglo dado `A`, donde cada elemento de `A` se incluye (en orden) con una probabilidad independiente `p`. (La complejidad es lineal en `p*length(A)`, por lo que esta función es eficiente incluso si `p` es pequeño y `A` es grande). Técnicamente, este proceso se conoce como "muestreo de Bernoulli" de `A`.

# Ejemplos

```jldoctest
julia> randsubseq(Xoshiro(123), 1:8, 0.3)
2-element Vector{Int64}:
 4
 7
```
