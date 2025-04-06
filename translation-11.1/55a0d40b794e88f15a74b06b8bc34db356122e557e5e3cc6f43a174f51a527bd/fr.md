```
randcycle([rng=default_rng(),] n::Integer)
```

Construit une permutation cyclique aléatoire de longueur `n`. L'argument optionnel `rng` spécifie un générateur de nombres aléatoires, voir [Random Numbers](@ref). Le type d'élément du résultat est le même que le type de `n`.

Ici, une "permutation cyclique" signifie que tous les éléments se trouvent dans un seul cycle. Si `n > 0`, il y a $(n-1)!$ permutations cycliques possibles, qui sont échantillonnées uniformément. Si `n == 0`, `randcycle` renvoie un vecteur vide.

[`randcycle!`](@ref) est une variante en place de cette fonction.

!!! compat "Julia 1.1"
    Dans Julia 1.1 et versions supérieures, `randcycle` renvoie un vecteur `v` avec `eltype(v) == typeof(n)` tandis que dans Julia 1.0 `eltype(v) == Int`.


# Exemples

```jldoctest
julia> randcycle(Xoshiro(123), 6)
6-element Vector{Int64}:
 5
 4
 2
 6
 3
 1
```
