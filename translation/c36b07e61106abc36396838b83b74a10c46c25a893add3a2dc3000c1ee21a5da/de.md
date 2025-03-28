```
diag(M, k::Integer=0)
```

Die `k`-te Diagonale einer Matrix, als Vektor.

Siehe auch [`diagm`](@ref), [`diagind`](@ref), [`Diagonal`](@ref), [`isdiag`](@ref).

# Beispiele

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> diag(A,1)
2-element Vector{Int64}:
 2
 6
```
