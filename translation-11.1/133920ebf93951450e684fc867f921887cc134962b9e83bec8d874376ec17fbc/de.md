```
randperm!([rng=default_rng(),] A::Array{<:Integer})
```

Konstruiere in `A` eine zufällige Permutation der Länge `length(A)`. Das optionale Argument `rng` gibt einen Zufallszahlengenerator an (siehe [Zufallszahlen](@ref)). Um einen beliebigen Vektor zufällig zu permutieren, siehe [`shuffle`](@ref) oder [`shuffle!`](@ref).

# Beispiele

```jldoctest
julia> randperm!(Xoshiro(123), Vector{Int}(undef, 4))
4-element Vector{Int64}:
 1
 4
 2
 3
```
