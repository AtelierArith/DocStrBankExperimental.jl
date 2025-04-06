```
schur(A) -> F::Schur
```

Matris `A`'nın Schur faktorizasyonunu hesaplar. (quasi) üçgen Schur faktörü, `F` Schur nesnesinden `F.Schur` veya `F.T` ile elde edilebilir ve ortogonal/unitary Schur vektörleri `F.vectors` veya `F.Z` ile elde edilebilir; böylece `A = F.vectors * F.Schur * F.vectors'`. `A`'nın özdeğerleri `F.values` ile elde edilebilir.

Gerçek `A` için Schur faktorizasyonu "quasitriangular"dır, bu da üst üçgen olduğu anlamına gelir, ancak karmaşık özdeğerlerin herhangi bir konjugat çifti için 2×2 diyagonal bloklar içerir; bu, karmaşık özdeğerler olsa bile faktorizasyonun tamamen gerçek olmasını sağlar. Gerçek bir quasitriangular faktorizasyondan (karmaşık) tamamen üst üçgen Schur faktorizasyonunu elde etmek için `Schur{Complex}(schur(A))` kullanabilirsiniz.

Ayrıştırmayı yinelemek, `F.T`, `F.Z` ve `F.values` bileşenlerini üretir.

# Örnekler

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> F = schur(A)
Schur{Float64, Matrix{Float64}, Vector{Float64}}
T faktörü:
2×2 Matrix{Float64}:
 3.0   9.0
 0.0  -2.0
Z faktörü:
2×2 Matrix{Float64}:
  0.961524  0.274721
 -0.274721  0.961524
özdeğerler:
2-element Vector{Float64}:
  3.0
 -2.0

julia> F.vectors * F.Schur * F.vectors'
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> t, z, vals = F; # yineleme ile parçalama

julia> t == F.T && z == F.Z && vals == F.values
true
```
