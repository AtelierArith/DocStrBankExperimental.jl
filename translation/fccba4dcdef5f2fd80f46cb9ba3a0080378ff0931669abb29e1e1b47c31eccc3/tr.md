```
CholeskyPivoted
```

Yoğun simetrik/Hermitian pozitif yarı-tam bir matris `A` için pivotlu Cholesky faktorizasyonunun matris faktorizasyon türü. Bu, [`cholesky(_, ::RowMaximum)`](@ref) ile ilgili matris faktorizasyon fonksiyonunun dönüş türüdür.

Üçgen Cholesky faktörü, faktorizasyon `F::CholeskyPivoted` üzerinden `F.L` ve `F.U` ile elde edilebilir ve permütasyon `F.p` ile elde edilir; burada `A[F.p, F.p] ≈ Ur' * Ur ≈ Lr * Lr'` ile `Ur = F.U[1:F.rank, :]` ve `Lr = F.L[:, 1:F.rank]`, veya alternatif olarak `A ≈ Up' * Up ≈ Lp * Lp'` ile `Up = F.U[1:F.rank, invperm(F.p)]` ve `Lp = F.L[invperm(F.p), 1:F.rank]`.

`CholeskyPivoted` nesneleri için aşağıdaki fonksiyonlar mevcuttur: [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref) ve [`rank`](@ref).

Ayrıştırma işlemi `L` ve `U` bileşenlerini üretir.

# Örnekler

```jldoctest
julia> X = [1.0, 2.0, 3.0, 4.0];

julia> A = X * X';

julia> C = cholesky(A, RowMaximum(), check = false)
CholeskyPivoted{Float64, Matrix{Float64}, Vector{Int64}}
U faktörü ile sıralama 1:
4×4 UpperTriangular{Float64, Matrix{Float64}}:
 4.0  2.0  3.0  1.0
  ⋅   0.0  6.0  2.0
  ⋅    ⋅   9.0  3.0
  ⋅    ⋅    ⋅   1.0
permutasyon:
4-elemanlı Vector{Int64}:
 4
 2
 3
 1

julia> C.U[1:C.rank, :]' * C.U[1:C.rank, :] ≈ A[C.p, C.p]
true

julia> l, u = C; # yineleme ile ayrıştırma

julia> l == C.L && u == C.U
true
```
