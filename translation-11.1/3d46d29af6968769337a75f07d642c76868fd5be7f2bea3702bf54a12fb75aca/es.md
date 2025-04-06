```
shuffle([rng=default_rng(),] v::AbstractArray)
```

Devuelve una copia de `v` aleatoriamente permutada. El argumento opcional `rng` especifica un generador de números aleatorios (ver [Números Aleatorios](@ref)). Para permutar `v` en su lugar, consulta [`shuffle!`](@ref). Para obtener índices aleatoriamente permutados, consulta [`randperm`](@ref).

# Ejemplos

```jldoctest
julia> shuffle(Xoshiro(123), Vector(1:10))
10-element Vector{Int64}:
  5
  4
  2
  3
  6
 10
  8
  1
  9
  7
```
