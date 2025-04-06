```
eachrow(A::AbstractVecOrMat) <: AbstractVector
```

Créez un objet [`RowSlices`](@ref) qui est un vecteur de lignes de la matrice ou du vecteur `A`. Les tranches de lignes sont retournées sous forme de vues `AbstractVector` de `A`.

Pour l'inverse, voir [`stack`](@ref)`(rows; dims=1)`.

Voir aussi [`eachcol`](@ref), [`eachslice`](@ref) et [`mapslices`](@ref).

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

julia> s = eachrow(a)
2-element RowSlices{Matrix{Int64}, Tuple{Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Int64, Base.Slice{Base.OneTo{Int64}}}, true}}:
 [1, 2]
 [3, 4]

julia> s[1]
2-element view(::Matrix{Int64}, 1, :) with eltype Int64:
 1
 2
```
