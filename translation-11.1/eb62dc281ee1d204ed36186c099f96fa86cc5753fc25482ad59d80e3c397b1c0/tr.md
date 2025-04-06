```
Diagonal(V::AbstractVector)
```

`V`'yi köşegen olarak kullanan tembel bir matris oluşturur.

Ayrıca, tembel bir kimlik matris olan `I` için [`UniformScaling`](@ref), yoğun bir matris oluşturmak için [`diagm`](@ref) ve köşegen elemanları çıkarmak için [`diag`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> d = Diagonal([1, 10, 100])
3×3 Diagonal{Int64, Vector{Int64}}:
 1   ⋅    ⋅
 ⋅  10    ⋅
 ⋅   ⋅  100

julia> diagm([7, 13])
2×2 Matrix{Int64}:
 7   0
 0  13

julia> ans + I
2×2 Matrix{Int64}:
 8   0
 0  14

julia> I(2)
2×2 Diagonal{Bool, Vector{Bool}}:
 1  ⋅
 ⋅  1
```

!!! not
    Tek sütunlu bir matris, bir vektör gibi işlenmez, bunun yerine `Diagonal(A::AbstractMatrix)` yöntemini çağırır ve `diag(A)` ile 1 eleman çıkarır:


```jldoctest
julia> A = transpose([7.0 13.0])
2×1 transpose(::Matrix{Float64}) with eltype Float64:
  7.0
 13.0

julia> Diagonal(A)
1×1 Diagonal{Float64, Vector{Float64}}:
 7.0
```
