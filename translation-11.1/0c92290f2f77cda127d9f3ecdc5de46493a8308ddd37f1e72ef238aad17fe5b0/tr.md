```
count([f=identity,] A::AbstractArray; dims=:)
```

`A` içindeki `f`'nin `true` döndürdüğü elemanların sayısını verilen boyutlar üzerinde sayar.

!!! compat "Julia 1.5"
    `dims` anahtar kelimesi Julia 1.5'te eklendi.


!!! compat "Julia 1.6"
    `init` anahtar kelimesi Julia 1.6'da eklendi.


# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> count(<=(2), A, dims=1)
1×2 Matrix{Int64}:
 1  1

julia> count(<=(2), A, dims=2)
2×1 Matrix{Int64}:
 2
 0
```
