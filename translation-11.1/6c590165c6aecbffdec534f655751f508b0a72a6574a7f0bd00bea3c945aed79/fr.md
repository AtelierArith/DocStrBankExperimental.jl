```
randsubseq!([rng=default_rng(),] S, A, p)
```

Comme [`randsubseq`](@ref), mais les résultats sont stockés dans `S` (qui est redimensionné si nécessaire).

# Exemples

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
