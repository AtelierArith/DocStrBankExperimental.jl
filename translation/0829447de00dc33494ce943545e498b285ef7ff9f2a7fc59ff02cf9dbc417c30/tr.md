```
sort!(A; dims::Integer, alg::Algorithm=defalg(A), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Çok boyutlu dizi `A`'yı `dims` boyutu boyunca sırala. Olası anahtar kelime argümanlarının açıklaması için [`sort!`](@ref) fonksiyonunun tek boyutlu versiyonuna bakın.

Bir dizinin dilimlerini sıralamak için [`sortslices`](@ref) fonksiyonuna başvurun.

!!! compat "Julia 1.1"
    Bu fonksiyon en az Julia 1.1 gerektirir.


# Örnekler

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
