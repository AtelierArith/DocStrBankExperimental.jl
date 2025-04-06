```
cholesky(A, RowMaximum(); tol = 0.0, check = true) -> CholeskyPivoted
```

Yoğun simetrik pozitif yarı-tam bir matris `A` için pivotlu Cholesky faktörizasyonunu hesaplayın ve bir [`CholeskyPivoted`](@ref) faktörizasyonu döndürün. Matris `A`, ya bir [`Symmetric`](@ref) ya da [`Hermitian`](@ref) [`AbstractMatrix`](@ref) veya *tamamen* simetrik veya Hermitian bir `AbstractMatrix` olabilir.

Faktörizasyondan `F` aracılığıyla üçgen Cholesky faktörü `F.L` ve `F.U` ile elde edilebilir ve permütasyon `F.p` ile elde edilir; burada `A[F.p, F.p] ≈ Ur' * Ur ≈ Lr * Lr'` ile `Ur = F.U[1:F.rank, :]` ve `Lr = F.L[:, 1:F.rank]`, veya alternatif olarak `A ≈ Up' * Up ≈ Lp * Lp'` ile `Up = F.U[1:F.rank, invperm(F.p)]` ve `Lp = F.L[invperm(F.p), 1:F.rank]`.

`CholeskyPivoted` nesneleri için aşağıdaki fonksiyonlar mevcuttur: [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref) ve [`rank`](@ref).

`tol` argümanı, rengi belirlemek için toleransı belirler. Negatif değerler için tolerans makine hassasiyetidir.

Eğer `A` matrisiniz, inşasında yuvarlama hataları nedeniyle hafifçe non-Hermitian ise, `cholesky` fonksiyonuna geçmeden önce `Hermitian(A)` ile sarmalayın, böylece onu tamamen Hermitian olarak ele alabilirsiniz.

`check = true` olduğunda, ayrıştırma başarısız olursa bir hata fırlatılır. `check = false` olduğunda, ayrıştırmanın geçerliliğini kontrol etme sorumluluğu (via [`issuccess`](@ref)) kullanıcıya aittir.

# Örnekler

```jldoctest
julia> X = [1.0, 2.0, 3.0, 4.0];

julia> A = X * X';

julia> C = cholesky(A, RowMaximum(), check = false)
CholeskyPivoted{Float64, Matrix{Float64}, Vector{Int64}}
U faktörü ile rengi 1:
4×4 UpperTriangular{Float64, Matrix{Float64}}:
 4.0  2.0  3.0  1.0
  ⋅   0.0  6.0  2.0
  ⋅    ⋅   9.0  3.0
  ⋅    ⋅    ⋅   1.0
permutasyon:
4-element Vector{Int64}:
 4
 2
 3
 1

julia> C.U[1:C.rank, :]' * C.U[1:C.rank, :] ≈ A[C.p, C.p]
true

julia> l, u = C; # iterasyon ile parçalama

julia> l == C.L && u == C.U
true
```
