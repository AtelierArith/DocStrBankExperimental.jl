```
seed!([rng=default_rng()], seed) -> rng
seed!([rng=default_rng()]) -> rng
```

Reinicializa el generador de números aleatorios: `rng` dará una secuencia reproducible de números si y solo si se proporciona una `semilla`. Algunos RNG no aceptan una semilla, como `RandomDevice`. Después de la llamada a `seed!`, `rng` es equivalente a un objeto recién creado inicializado con la misma semilla. Los tipos de semillas aceptadas dependen del tipo de `rng`, pero en general, las semillas enteras deberían funcionar.

Si `rng` no se especifica, se inicializa el estado del generador local compartido por defecto.

# Ejemplos

```julia-repl
julia> Random.seed!(1234);

julia> x1 = rand(2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> Random.seed!(1234);

julia> x2 = rand(2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> x1 == x2
true

julia> rng = Xoshiro(1234); rand(rng, 2) == x1
true

julia> Xoshiro(1) == Random.seed!(rng, 1)
true

julia> rand(Random.seed!(rng), Bool) # no reproducible
true

julia> rand(Random.seed!(rng), Bool) # tampoco reproducible
false

julia> rand(Xoshiro(), Bool) # tampoco reproducible
true
```
