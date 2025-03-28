```
randperm([rng=default_rng(),] n::Integer)
```

Construit une permutation aléatoire de longueur `n`. L'argument optionnel `rng` spécifie un générateur de nombres aléatoires (voir [Random Numbers](@ref)). Le type d'élément du résultat est le même que le type de `n`.

Pour permuter aléatoirement un vecteur arbitraire, voir [`shuffle`](@ref) ou [`shuffle!`](@ref).

!!! compat "Julia 1.1"
    Dans Julia 1.1, `randperm` renvoie un vecteur `v` avec `eltype(v) == typeof(n)` tandis que dans Julia 1.0, `eltype(v) == Int`.


# Exemples

```jldoctest
julia> randperm(Xoshiro(123), 4)
4-element Vector{Int64}:
 1
 4
 2
 3
```
