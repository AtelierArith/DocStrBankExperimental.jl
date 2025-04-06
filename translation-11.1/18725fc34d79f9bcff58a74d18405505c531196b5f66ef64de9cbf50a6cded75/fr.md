```
view(A, inds...)
```

Comme [`getindex`](@ref), mais renvoie un tableau léger qui référence paresseusement (ou est effectivement une *vue* sur) le tableau parent `A` à l'index ou aux indices donnés `inds` au lieu d'extraire les éléments de manière anticipée ou de construire un sous-ensemble copié. Appeler [`getindex`](@ref) ou [`setindex!`](@ref) sur la valeur renvoyée (souvent un [`SubArray`](@ref)) calcule les indices pour accéder ou modifier le tableau parent à la volée. Le comportement est indéfini si la forme du tableau parent est modifiée après l'appel de `view` car il n'y a pas de vérification de limite pour le tableau parent ; par exemple, cela peut provoquer une erreur de segmentation.

Certains tableaux parents immuables (comme les plages) peuvent choisir de simplement recalculer un nouveau tableau dans certaines circonstances au lieu de renvoyer un `SubArray` si cela est efficace et fournit une sémantique compatible.

!!! compat "Julia 1.6"
    Dans Julia 1.6 ou ultérieur, `view` peut être appelé sur un `AbstractString`, renvoyant un `SubString`.


# Exemples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> b = view(A, :, 1)
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 1
 3

julia> fill!(b, 0)
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 0
 0

julia> A # Notez que A a changé même si nous avons modifié b
2×2 Matrix{Int64}:
 0  2
 0  4

julia> view(2:5, 2:3) # renvoie une plage car le type est immuable
3:4
```
