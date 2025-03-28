```
sort(A; dims::Integer, alg::Algorithm=defalg(A), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Sortiere ein mehrdimensionales Array `A` entlang der angegebenen Dimension. Siehe [`sort!`](@ref) für eine Beschreibung der möglichen Schlüsselwortargumente.

Um Teile eines Arrays zu sortieren, siehe [`sortslices`](@ref).

# Beispiele

```jldoctest
julia> A = [4 3; 1 2]
2×2 Matrix{Int64}:
 4  3
 1  2

julia> sort(A, dims = 1)
2×2 Matrix{Int64}:
 1  2
 4  3

julia> sort(A, dims = 2)
2×2 Matrix{Int64}:
 3  4
 1  2
```
