```
Xoshiro(seed::Union{Integer, AbstractString})
Xoshiro()
```

Xoshiro256++ es un generador de números pseudorandom rápidos descrito por David Blackman y Sebastiano Vigna en "Scrambled Linear Pseudorandom Number Generators", ACM Trans. Math. Softw., 2021. La implementación de referencia está disponible en https://prng.di.unimi.it

Aparte de la alta velocidad, Xoshiro tiene una pequeña huella de memoria, lo que lo hace adecuado para aplicaciones donde se necesitan mantener muchos estados aleatorios diferentes durante mucho tiempo.

La implementación de Xoshiro en Julia tiene un modo de generación masiva; esto siembra nuevos PRNG virtuales desde el padre y utiliza SIMD para generar en paralelo (es decir, el flujo masivo consiste en múltiples instancias de xoshiro entrelazadas). Los PRNG virtuales se descartan una vez que se ha atendido la solicitud masiva (y no deberían causar asignaciones en el heap).

Si no se proporciona una semilla, se crea una generada aleatoriamente (utilizando la entropía del sistema). Consulte la función [`seed!`](@ref) para volver a sembrar un objeto `Xoshiro` ya existente.

!!! compat "Julia 1.11"
    Pasar una semilla entera negativa requiere al menos Julia 1.11.


# Ejemplos

```jldoctest
julia> using Random

julia> rng = Xoshiro(1234);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> rng = Xoshiro(1234);

julia> x2 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> x1 == x2
true
```
