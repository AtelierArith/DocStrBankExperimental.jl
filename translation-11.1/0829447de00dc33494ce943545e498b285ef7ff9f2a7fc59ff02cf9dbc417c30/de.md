```
sort!(A; dims::Integer, alg::Algorithm=defalg(A), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Sortiere das mehrdimensionale Array `A` entlang der Dimension `dims`. Siehe die eindimensionale Version von [`sort!`](@ref) für eine Beschreibung der möglichen Schlüsselwortargumente.

Um Teile eines Arrays zu sortieren, verweisen Sie auf [`sortslices`](@ref).

!!! compat "Julia 1.1"
    Diese Funktion erfordert mindestens Julia 1.1.


# Beispiele

```jldoctest
julia> A = [4 3; 1 2]
2×2 Matrix{Int64}:
 4  3
 1  2

julia> sort!(A, dims = 1); A
2×2 Matrix{Int64}:
 1  2
 4  3

julia> sort!(A, dims = 2); A
2×2 Matrix{Int64}:
 1  2
 3  4
```
