```
eachslice(A::AbstractArray; dims, drop=true)
```

Créez un objet [`Slices`](@ref) qui est un tableau de tranches sur les dimensions `dims` de `A`, retournant des vues qui sélectionnent toutes les données des autres dimensions dans `A`. `dims` peut être soit un entier, soit un tuple d'entiers.

Si `drop = true` (par défaut), le `Slices` extérieur supprimera les dimensions intérieures, et l'ordre des dimensions correspondra à celles de `dims`. Si `drop = false`, alors le `Slices` aura la même dimensionalité que le tableau sous-jacent, avec des dimensions intérieures de taille 1.

Voir [`stack`](@ref)`(slices; dims)` pour l'inverse de `eachslice(A; dims::Integer)`.

Voir aussi [`eachrow`](@ref), [`eachcol`](@ref), [`mapslices`](@ref) et [`selectdim`](@ref).

!!! compat "Julia 1.1"
    Cette fonction nécessite au moins Julia 1.1.


!!! compat "Julia 1.9"
    Avant Julia 1.9, cela retournait un itérateur, et seule une dimension `dims` était supportée.


# Exemples

```jldoctest
julia> m = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> s = eachslice(m, dims=1)
3-element RowSlices{Matrix{Int64}, Tuple{Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Int64, Base.Slice{Base.OneTo{Int64}}}, true}}:
 [1, 2, 3]
 [4, 5, 6]
 [7, 8, 9]

julia> s[1]
3-element view(::Matrix{Int64}, 1, :) with eltype Int64:
 1
 2
 3

julia> eachslice(m, dims=1, drop=false)
3×1 Slices{Matrix{Int64}, Tuple{Int64, Colon}, Tuple{Base.OneTo{Int64}, Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Int64, Base.Slice{Base.OneTo{Int64}}}, true}, 2}:
 [1, 2, 3]
 [4, 5, 6]
 [7, 8, 9]
```
