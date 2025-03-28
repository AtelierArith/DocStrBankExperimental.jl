```
diagm(kv::Pair{<:Integer,<:AbstractVector}...)
diagm(m::Integer, n::Integer, kv::Pair{<:Integer,<:AbstractVector}...)

Construit une matrice à partir de `Pair`s de diagonales et de vecteurs. Le vecteur `kv.second` sera placé sur la diagonale `kv.first`. Par défaut, la matrice est carrée et sa taille est déduite de `kv`, mais une taille non carrée `m`×`n` (remplie de zéros si nécessaire) peut être spécifiée en passant `m,n` comme premiers arguments. Pour les indices de diagonale répétés `kv.first`, les valeurs des vecteurs correspondants `kv.second` seront additionnées.

`diagm` construit une matrice complète ; si vous souhaitez des versions économes en stockage avec une arithmétique rapide, consultez [`Diagonal`](@ref), [`Bidiagonal`](@ref), [`Tridiagonal`](@ref) et [`SymTridiagonal`](@ref).

# Exemples

```

jldoctest julia> diagm(1 => [1,2,3]) 4×4 Matrix{Int64}:  0  1  0  0  0  0  2  0  0  0  0  3  0  0  0  0

julia> diagm(1 => [1,2,3], -1 => [4,5]) 4×4 Matrix{Int64}:  0  1  0  0  4  0  2  0  0  5  0  3  0  0  0  0

julia> diagm(1 => [1,2,3], 1 => [1,2,3]) 4×4 Matrix{Int64}:  0  2  0  0  0  0  4  0  0  0  0  6  0  0  0  0 ```
