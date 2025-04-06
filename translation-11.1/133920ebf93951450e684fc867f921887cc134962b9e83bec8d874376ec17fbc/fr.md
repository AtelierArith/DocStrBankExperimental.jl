```
randperm!([rng=default_rng(),] A::Array{<:Integer})
```

Construit dans `A` une permutation aléatoire de longueur `length(A)`. L'argument optionnel `rng` spécifie un générateur de nombres aléatoires (voir [Nombres aléatoires](@ref)). Pour permuter aléatoirement un vecteur arbitraire, voir [`shuffle`](@ref) ou [`shuffle!`](@ref).

# Exemples

```jldoctest
julia> randperm!(Xoshiro(123), Vector{Int}(undef, 4))
4-element Vector{Int64}:
 1
 4
 2
 3
```
