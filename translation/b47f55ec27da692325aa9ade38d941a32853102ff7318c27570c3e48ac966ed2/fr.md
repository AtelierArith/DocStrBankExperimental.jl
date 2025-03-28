```
randstring([rng=default_rng()], [chars], [len=8])
```

Crée une chaîne aléatoire de longueur `len`, composée de caractères de `chars`, qui par défaut est l'ensemble des lettres majuscules et minuscules et des chiffres 0-9. L'argument optionnel `rng` spécifie un générateur de nombres aléatoires, voir [Random Numbers](@ref).

# Exemples

```jldoctest
julia> Random.seed!(3); randstring()
"Lxz5hUwn"

julia> randstring(Xoshiro(3), 'a':'z', 6)
"iyzcsm"

julia> randstring("ACGT")
"TGCTCCTC"
```

!!! note
    `chars` peut être n'importe quelle collection de caractères, de type `Char` ou `UInt8` (plus efficace), à condition que [`rand`](@ref) puisse choisir des caractères au hasard à partir de celle-ci.

