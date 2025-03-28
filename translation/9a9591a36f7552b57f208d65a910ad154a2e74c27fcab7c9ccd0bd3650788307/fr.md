```
copy(A::Transpose)
copy(A::Adjoint)
```

Évaluez avec empressement la transposition/adjointe de matrice paresseuse. Notez que la transposition est appliquée de manière récursive aux éléments.

Cette opération est destinée à un usage en algèbre linéaire - pour une manipulation générale des données, voir [`permutedims`](@ref Base.permutedims), qui est non récursive.

# Exemples

```jldoctest
julia> A = [1 2im; -3im 4]
2×2 Matrix{Complex{Int64}}:
 1+0im  0+2im
 0-3im  4+0im

julia> T = transpose(A)
2×2 transpose(::Matrix{Complex{Int64}}) with eltype Complex{Int64}:
 1+0im  0-3im
 0+2im  4+0im

julia> copy(T)
2×2 Matrix{Complex{Int64}}:
 1+0im  0-3im
 0+2im  4+0im
```
