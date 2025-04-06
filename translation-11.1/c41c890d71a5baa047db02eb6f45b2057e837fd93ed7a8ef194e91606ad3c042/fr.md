```
randn([rng=default_rng()], [T=Float64], [dims...])
```

Génère un nombre aléatoire distribué normalement de type `T` avec une moyenne de 0 et un écart type de 1. Étant donné les arguments `dims` optionnels, générez un tableau de taille `dims` de tels nombres. La bibliothèque standard de Julia prend en charge `randn` pour tout type à virgule flottante qui implémente [`rand`](@ref), par exemple les types `Base` [`Float16`](@ref), [`Float32`](@ref), [`Float64`](@ref) (le défaut), et [`BigFloat`](@ref), ainsi que leurs homologues [`Complex`](@ref).

(Lorsque `T` est complexe, les valeurs sont tirées de la distribution normale complexe circulairement symétrique de variance 1, correspondant à des parties réelles et imaginaires ayant une distribution normale indépendante avec une moyenne de zéro et une variance de `1/2`).

Voir aussi [`randn!`](@ref) pour agir en place.

# Exemples

Génération d'un seul nombre aléatoire (avec le type par défaut `Float64`) :

```julia-repl
julia> randn()
-0.942481877315864
```

Génération d'une matrice de nombres aléatoires normaux (avec le type par défaut `Float64`) :

```julia-repl
julia> randn(2,3)
2×3 Matrix{Float64}:
  1.18786   -0.678616   1.49463
 -0.342792  -0.134299  -1.45005
```

Configuration du générateur de nombres aléatoires `rng` avec une graine définie par l'utilisateur (pour des nombres reproductibles) et utilisation de celui-ci pour générer un nombre aléatoire `Float32` ou une matrice de nombres aléatoires `ComplexF32` :

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> randn(rng, Float32)
-0.6457307f0

julia> randn(rng, ComplexF32, (2, 3))
2×3 Matrix{ComplexF32}:
  -1.03467-1.14806im  0.693657+0.056538im   0.291442+0.419454im
 -0.153912+0.34807im    1.0954-0.948661im  -0.543347-0.0538589im
```
