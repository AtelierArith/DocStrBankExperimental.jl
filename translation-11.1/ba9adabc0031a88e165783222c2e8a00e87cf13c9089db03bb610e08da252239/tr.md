```
Eigen <: Factorization
```

Kare matris `A`'nın özdeğer/spektral ayrıştırma matris ayrıştırma türüdür. Bu, [`eigen`](@ref) olan ilgili matris ayrıştırma fonksiyonunun dönüş türüdür.

Eğer `F::Eigen` ayrıştırma nesnesi ise, özdeğerler `F.values` aracılığıyla elde edilebilir ve özvektörler `F.vectors` matrisinin sütunları olarak elde edilebilir. (`k`'nci özvektör `F.vectors[:, k]` diliminden elde edilebilir.)

Ayrıştırmayı yinelemek, `F.values` ve `F.vectors` bileşenlerini üretir.

# Örnekler

```jldoctest
julia> F = eigen([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
Eigen{Float64, Float64, Matrix{Float64}, Vector{Float64}}
values:
3-element Vector{Float64}:
  1.0
  3.0
 18.0
vectors:
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> F.values
3-element Vector{Float64}:
  1.0
  3.0
 18.0

julia> F.vectors
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> vals, vecs = F; # destructuring via iteration

julia> vals == F.values && vecs == F.vectors
true
```
