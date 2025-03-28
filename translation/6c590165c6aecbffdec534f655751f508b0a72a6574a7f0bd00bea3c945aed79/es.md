```
randsubseq!([rng=default_rng(),] S, A, p)
```

Como [`randsubseq`](@ref), pero los resultados se almacenan en `S` (que se redimensiona según sea necesario).

# Ejemplos

```jldoctest
julia> S = Int64[];

julia> randsubseq!(Xoshiro(123), S, 1:8, 0.3)
2-element Vector{Int64}:
 4
 7

julia> S
2-element Vector{Int64}:
 4
 7
```
