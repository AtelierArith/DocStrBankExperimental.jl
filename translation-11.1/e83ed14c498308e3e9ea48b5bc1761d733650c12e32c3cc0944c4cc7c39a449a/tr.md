```
sort(A; dims::Integer, alg::Algorithm=defalg(A), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Verilen boyut boyunca çok boyutlu bir dizi `A`'yı sırala. Olası anahtar kelime argümanlarının açıklaması için [`sort!`](@ref) kısmına bakın.

Bir dizinin dilimlerini sıralamak için [`sortslices`](@ref) kısmına başvurun.

# Örnekler

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
