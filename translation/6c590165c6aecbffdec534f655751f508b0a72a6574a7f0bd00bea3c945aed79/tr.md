```
randsubseq!([rng=default_rng(),] S, A, p)
```

[`randsubseq`](@ref) gibi, ancak sonuçlar `S` içinde saklanır (gerekirse boyutu değiştirilir).

# Örnekler

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
