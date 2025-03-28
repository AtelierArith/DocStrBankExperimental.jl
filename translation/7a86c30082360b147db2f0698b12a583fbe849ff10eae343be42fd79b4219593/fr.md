```
Xoshiro(seed::Union{Integer, AbstractString})
Xoshiro()
```

Xoshiro256++ est un générateur de nombres pseudorandom rapides décrit par David Blackman et Sebastiano Vigna dans "Scrambled Linear Pseudorandom Number Generators", ACM Trans. Math. Softw., 2021. L'implémentation de référence est disponible à https://prng.di.unimi.it

En plus de sa grande vitesse, Xoshiro a une petite empreinte mémoire, ce qui le rend adapté aux applications où de nombreux états aléatoires différents doivent être conservés pendant longtemps.

L'implémentation de Xoshiro en Julia dispose d'un mode de génération en masse ; cela sème de nouveaux PRNG virtuels à partir du parent et utilise SIMD pour générer en parallèle (c'est-à-dire que le flux en masse consiste en plusieurs instances de xoshiro entrelacées). Les PRNG virtuels sont éliminés une fois la demande en masse traitée (et ne devraient pas entraîner d'allocations de tas).

Si aucun semence n'est fournie, une semence générée aléatoirement est créée (en utilisant l'entropie du système). Voir la fonction [`seed!`](@ref) pour re-semer un objet `Xoshiro` déjà existant.

!!! compat "Julia 1.11"
    Passer une semence entière négative nécessite au moins Julia 1.11.


# Exemples

```jldoctest
julia> using Random

julia> rng = Xoshiro(1234);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> rng = Xoshiro(1234);

julia> x2 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> x1 == x2
true
```
