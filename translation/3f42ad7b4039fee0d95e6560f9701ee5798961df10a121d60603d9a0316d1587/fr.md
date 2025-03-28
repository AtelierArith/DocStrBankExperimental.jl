```
Array{T}(undef, dims)
Array{T,N}(undef, dims)
```

Construit un tableau `N`-dimensionnel non initialisé [`Array`](@ref) contenant des éléments de type `T`. `N` peut être fourni explicitement, comme dans `Array{T,N}(undef, dims)`, ou être déterminé par la longueur ou le nombre de `dims`. `dims` peut être un tuple ou une série d'arguments entiers correspondant aux longueurs dans chaque dimension. Si le rang `N` est fourni explicitement, il doit correspondre à la longueur ou au nombre de `dims`. Ici, [`undef`](@ref) est le [`UndefInitializer`](@ref).

# Exemples

```julia-repl
julia> A = Array{Float64, 2}(undef, 2, 3) # N donné explicitement
2×3 Matrix{Float64}:
 6.90198e-310  6.90198e-310  6.90198e-310
 6.90198e-310  6.90198e-310  0.0

julia> B = Array{Float64}(undef, 4) # N déterminé par l'entrée
4-element Vector{Float64}:
   2.360075077e-314
 NaN
   2.2671131793e-314
   2.299821756e-314

julia> similar(B, 2, 4, 1) # utilise typeof(B), et la taille donnée
2×4×1 Array{Float64, 3}:
[:, :, 1] =
 2.26703e-314  2.26708e-314  0.0           2.80997e-314
 0.0           2.26703e-314  2.26708e-314  0.0
```
