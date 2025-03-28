```
shuffle!([rng=default_rng(),] v::AbstractArray)
```

Versión en su lugar de [`shuffle`](@ref): permuta aleatoriamente `v` en su lugar, opcionalmente suministrando el generador de números aleatorios `rng`.

# Ejemplos

```jldoctest
julia> shuffle!(Xoshiro(123), Vector(1:10))
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
