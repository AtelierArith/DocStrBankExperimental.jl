```
GenelleştirilmişEigen <: Faktörizasyon
```

`A` ve `B`'nin genelleştirilmiş özdeğer/spektral ayrıştırmasının matris faktörizasyon türü. Bu, iki matris argümanıyla çağrıldığında [`eigen`](@ref) ile ilgili matris faktörizasyon fonksiyonunun dönüş türüdür.

Eğer `F::GenelleştirilmişEigen` faktörizasyon nesnesi ise, özdeğerler `F.values` aracılığıyla elde edilebilir ve özvektörler `F.vectors` matrisinin sütunları olarak elde edilebilir. (`k`'nci özvektör `F.vectors[:, k]` diliminden elde edilebilir.)

Ayrıştırmayı yinelemek, `F.values` ve `F.vectors` bileşenlerini üretir.

# Örnekler

```jldoctest
julia> A = [1 0; 0 -1]
2×2 Matrix{Int64}:
 1   0
 0  -1

julia> B = [0 1; 1 0]
2×2 Matrix{Int64}:
 0  1
 1  0

julia> F = eigen(A, B)
GenelleştirilmişEigen{ComplexF64, ComplexF64, Matrix{ComplexF64}, Vector{ComplexF64}}
values:
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im
vectors:
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> F.values
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> F.vectors
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> vals, vecs = F; # destructuring via iteration

julia> vals == F.values && vecs == F.vectors
true
```
