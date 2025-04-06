```
MersenneTwister(seed)
MersenneTwister()
```

Crea un objeto RNG `MersenneTwister`. Diferentes objetos RNG pueden tener sus propias semillas, lo que puede ser útil para generar diferentes secuencias de números aleatorios. La `seed` puede ser un entero, una cadena o un vector de enteros `UInt32`. Si no se proporciona una semilla, se crea una generada aleatoriamente (utilizando la entropía del sistema). Consulta la función [`seed!`](@ref) para volver a sembrar un objeto `MersenneTwister` ya existente.

!!! compat "Julia 1.11"
    Pasar una semilla entera negativa requiere al menos Julia 1.11.


# Ejemplos

```jldoctest
julia> rng = MersenneTwister(123);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.37453777969575874
 0.8735343642013971

julia> x2 = rand(MersenneTwister(123), 2)
2-element Vector{Float64}:
 0.37453777969575874
 0.8735343642013971

julia> x1 == x2
true
```
