```
sprandn([rng][,Type],m[,n],p::AbstractFloat)
```

Crée un vecteur sparse aléatoire de longueur `m` ou une matrice sparse de taille `m` par `n` avec la probabilité (indépendante) spécifiée `p` qu'une entrée soit non nulle, où les valeurs non nulles sont échantillonnées à partir de la distribution normale. L'argument optionnel `rng` spécifie un générateur de nombres aléatoires, voir [Random Numbers](@ref).

!!! compat "Julia 1.1"
    La spécification du type d'élément de sortie `Type` nécessite au moins Julia 1.1.


# Exemples

```jldoctest; setup = :(using Random; Random.seed!(0))
julia> sprandn(2, 2, 0.75)
2×2 SparseMatrixCSC{Float64, Int64} avec 3 entrées stockées :
 -1.20577     ⋅
  0.311817  -0.234641
```
