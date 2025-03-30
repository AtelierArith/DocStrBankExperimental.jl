```
extrema(A::AbstractArray; dims) -> Array{Tuple}
```

Verilen boyutlar üzerinde bir dizinin minimum ve maksimum elemanlarını hesaplar.

Ayrıca bakınız: [`minimum`](@ref), [`maximum`](@ref), [`extrema!`](@ref).

# Örnekler

```jldoctest
julia> A = reshape(Vector(1:2:16), (2,2,2))
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  5
 3  7

[:, :, 2] =
  9  13
 11  15

julia> extrema(A, dims = (1,2))
1×1×2 Array{Tuple{Int64, Int64}, 3}:
[:, :, 1] =
 (1, 7)

[:, :, 2] =
 (9, 15)
```
