```
sortperm(A; alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward, [dims::Integer])
```

Gibt einen Permutationsvektor oder -array `I` zurück, der `A[I]` in sortierter Reihenfolge entlang der angegebenen Dimension anordnet. Wenn `A` mehr als eine Dimension hat, muss das Schlüsselwortargument `dims` angegeben werden. Die Reihenfolge wird mit denselben Schlüsselwörtern wie bei [`sort!`](@ref) angegeben. Die Permutation ist garantiert stabil, auch wenn der Sortieralgorithmus instabil ist: die Indizes von gleichen Elementen erscheinen in aufsteigender Reihenfolge.

Siehe auch [`sortperm!`](@ref), [`partialsortperm`](@ref), [`invperm`](@ref), [`indexin`](@ref). Um Teile eines Arrays zu sortieren, verweisen Sie auf [`sortslices`](@ref).

!!! compat "Julia 1.9"
    Die Methode, die `dims` akzeptiert, erfordert mindestens Julia 1.9.


# Beispiele

```jldoctest
julia> v = [3, 1, 2];

julia> p = sortperm(v)
3-element Vector{Int64}:
 2
 3
 1

julia> v[p]
3-element Vector{Int64}:
 1
 2
 3

julia> A = [8 7; 5 6]
2×2 Matrix{Int64}:
 8  7
 5  6

julia> sortperm(A, dims = 1)
2×2 Matrix{Int64}:
 2  4
 1  3

julia> sortperm(A, dims = 2)
2×2 Matrix{Int64}:
 3  1
 2  4
```
