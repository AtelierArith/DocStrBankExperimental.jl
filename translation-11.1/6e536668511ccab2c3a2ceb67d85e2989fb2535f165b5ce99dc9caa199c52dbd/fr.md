```
diagind(M::AbstractMatrix, k::Integer = 0, indstyle::IndexStyle = IndexLinear())
diagind(M::AbstractMatrix, indstyle::IndexStyle = IndexLinear())
```

Un `AbstractRange` donnant les indices de la `k`-ième diagonale de la matrice `M`. En option, un style d'index peut être spécifié, ce qui détermine le type de la plage retournée. Si `indstyle isa IndexLinear` (par défaut), cela retourne un `AbstractRange{Integer}`. D'autre part, si `indstyle isa IndexCartesian`, cela retourne un `AbstractRange{CartesianIndex{2}}`.

Si `k` n'est pas fourni, il est supposé être `0` (correspondant à la diagonale principale).

Voir aussi : [`diag`](@ref), [`diagm`](@ref), [`Diagonal`](@ref).

# Exemples

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> diagind(A, -1)
2:4:6

julia> diagind(A, IndexCartesian())
StepRangeLen(CartesianIndex(1, 1), CartesianIndex(1, 1), 3)
```

!!! compat "Julia 1.11"
    Spécifier un `IndexStyle` nécessite au moins Julia 1.11.

