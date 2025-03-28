```
MersenneTwister(seed)
MersenneTwister()
```

Créez un objet RNG `MersenneTwister`. Différents objets RNG peuvent avoir leurs propres graines, ce qui peut être utile pour générer différents flux de nombres aléatoires. La `seed` peut être un entier, une chaîne de caractères ou un vecteur d'entiers `UInt32`. Si aucune graine n'est fournie, une graine générée aléatoirement est créée (en utilisant l'entropie du système). Consultez la fonction [`seed!`](@ref) pour réinitialiser une graine d'un objet `MersenneTwister` déjà existant.

!!! compat "Julia 1.11"
    Passer une graine entière négative nécessite au moins Julia 1.11.


# Exemples

```jldoctest
julia> rng = MersenneTwister(123);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.37453777969575874
 0.8735343642013971

julia> x2 = rand(MersenneTwister(123), 2)
2-element Vector{Float64}:
 0.37453777969575874
 0.8735343642013971

julia> x1 == x2
true
```
