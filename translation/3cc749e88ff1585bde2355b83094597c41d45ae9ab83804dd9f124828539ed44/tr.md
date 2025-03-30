```
Cholesky <: Factorizasyon
```

Yoğun simetrik/Hermitian pozitif belirli matris `A` için Cholesky faktorizasyonunun matris faktorizasyon türü. Bu, [`cholesky`](@ref) ile ilgili matris faktorizasyon fonksiyonunun dönüş türüdür.

Üçgen Cholesky faktörü, faktorizasyon `F::Cholesky` üzerinden `F.L` ve `F.U` ile elde edilebilir; burada `A ≈ F.U' * F.U ≈ F.L * F.L'`.

`Cholesky` nesneleri için aşağıdaki fonksiyonlar mevcuttur: [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref), [`logdet`](@ref) ve [`isposdef`](@ref).

Ayrıştırmayı yinelemek, `L` ve `U` bileşenlerini üretir.

# Örnekler

```jldoctest
julia> A = [4. 12. -16.; 12. 37. -43.; -16. -43. 98.]
3×3 Matrix{Float64}:
   4.0   12.0  -16.0
  12.0   37.0  -43.0
 -16.0  -43.0   98.0

julia> C = cholesky(A)
Cholesky{Float64, Matrix{Float64}}
U faktörü:
3×3 UpperTriangular{Float64, Matrix{Float64}}:
 2.0  6.0  -8.0
  ⋅   1.0   5.0
  ⋅    ⋅    3.0

julia> C.U
3×3 UpperTriangular{Float64, Matrix{Float64}}:
 2.0  6.0  -8.0
  ⋅   1.0   5.0
  ⋅    ⋅    3.0

julia> C.L
3×3 LowerTriangular{Float64, Matrix{Float64}}:
  2.0   ⋅    ⋅
  6.0  1.0   ⋅
 -8.0  5.0  3.0

julia> C.L * C.U == A
true

julia> l, u = C; # yineleme ile parçalama

julia> l == C.L && u == C.U
true
```
