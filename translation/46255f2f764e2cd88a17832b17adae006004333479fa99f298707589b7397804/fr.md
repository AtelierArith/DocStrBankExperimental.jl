```
eachcol(A::AbstractVecOrMat) <: AbstractVector
```

Créez un objet [`ColumnSlices`](@ref) qui est un vecteur de colonnes de la matrice ou du vecteur `A`. Les tranches de colonnes sont retournées sous forme de vues `AbstractVector` de `A`.

Pour l'inverse, voir [`stack`](@ref)`(cols)` ou `reduce(`[`hcat`](@ref)`, cols)`.

Voir aussi [`eachrow`](@ref), [`eachslice`](@ref) et [`mapslices`](@ref).

!!! compat "Julia 1.1"
    Cette fonction nécessite au moins Julia 1.1.


!!! compat "Julia 1.9"
    Avant Julia 1.9, cela retournait un itérateur.


# Exemples

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> s = eachcol(a)
2-element ColumnSlices{Matrix{Int64}, Tuple{Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Base.Slice{Base.OneTo{Int64}}, Int64}, true}}:
 [1, 3]
 [2, 4]

julia> s[1]
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 1
 3
```
