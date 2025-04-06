```
sprand([rng],[T::Type],m,[n],p::AbstractFloat)
sprand([rng],m,[n],p::AbstractFloat,[rfn=rand])
```

Créez un vecteur sparse de longueur aléatoire `m` ou une matrice sparse de `m` par `n`, dans laquelle la probabilité qu'un élément soit non nul est indépendamment donnée par `p` (et donc la densité moyenne des non-nuls est également exactement `p`). L'argument optionnel `rng` spécifie un générateur de nombres aléatoires, voir [Random Numbers](@ref). L'argument optionnel `T` spécifie le type d'élément, qui par défaut est `Float64`.

Par défaut, les valeurs non nulles sont échantillonnées à partir d'une distribution uniforme en utilisant la fonction [`rand`](@ref), c'est-à-dire par `rand(T)`, ou `rand(rng, T)` si `rng` est fourni ; pour le `T=Float64` par défaut, cela correspond à des valeurs non nulles échantillonnées uniformément dans `[0,1)`.

Vous pouvez échantillonner des valeurs non nulles à partir d'une distribution différente en passant une fonction `rfn` personnalisée au lieu de `rand`. Cela devrait être une fonction `rfn(k)` qui retourne un tableau de `k` nombres aléatoires échantillonnés à partir de la distribution souhaitée ; alternativement, si `rng` est fourni, cela devrait plutôt être une fonction `rfn(rng, k)`.

# Exemples

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> sprand(Bool, 2, 2, 0.5)
2×2 SparseMatrixCSC{Bool, Int64} avec 2 entrées stockées :
 1  1
 ⋅  ⋅

julia> sprand(Float64, 3, 0.75)
3-élément SparseVector{Float64, Int64} avec 2 entrées stockées :
  [1]  =  0.795547
  [2]  =  0.49425
```
