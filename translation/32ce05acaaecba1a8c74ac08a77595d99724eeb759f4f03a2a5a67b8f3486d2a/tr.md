```
sortperm(A; alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward, [dims::Integer])
```

Bir sıralama vektörü veya dizisi `I` döndürür ki bu da `A[I]`'yi belirtilen boyutta sıralı hale getirir. Eğer `A` birden fazla boyuta sahipse, `dims` anahtar kelime argümanı belirtilmelidir. Sıralama, [`sort!`](@ref) ile aynı anahtar kelimeleri kullanarak belirtilir. Permutasyon, sıralama algoritması kararsız olsa bile kararlıdır: eşit elemanların indeksleri artan sırada görünecektir.

Ayrıca [`sortperm!`](@ref), [`partialsortperm`](@ref), [`invperm`](@ref), [`indexin`](@ref) ile de ilgili. Bir dizinin dilimlerini sıralamak için, [`sortslices`](@ref) referansına bakın.

!!! compat "Julia 1.9"
    `dims` kabul eden yöntem en az Julia 1.9 gerektirir.


# Örnekler

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
