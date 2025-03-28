```
randcycle!([rng=default_rng(),] A::Array{<:Integer})
```

Construit dans `A` une permutation cyclique aléatoire de longueur `n = length(A)`. L'argument optionnel `rng` spécifie un générateur de nombres aléatoires, voir [Random Numbers](@ref).

Ici, une "permutation cyclique" signifie que tous les éléments se trouvent dans un seul cycle. Si `A` n'est pas vide (`n > 0`), il y a $(n-1)!$ permutations cycliques possibles, qui sont échantillonnées uniformément. Si `A` est vide, `randcycle!` le laisse inchangé.

[`randcycle`](@ref) est une variante de cette fonction qui alloue un nouveau vecteur.

# Exemples

```jldoctest
julia> randcycle!(Xoshiro(123), Vector{Int}(undef, 6))
6-element Vector{Int64}:
 5
 4
 2
 6
 3
 1
```
