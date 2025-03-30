```
cholesky(A::SparseMatrixCSC; shift = 0.0, check = true, perm = nothing) -> CHOLMOD.Factor
```

Sıkı pozitif belirli bir matris `A`'nın Cholesky faktörizasyonunu hesaplar. `A`, bir [`SparseMatrixCSC`](@ref) veya bir [`Symmetric`](@ref)/[`Hermitian`](@ref) görünümü olmalıdır. `A`'nın tür etiketi olmasa bile, hala simetrik veya Hermitian olması gerekir. `perm` verilmemişse, bir dolgu azaltıcı permütasyon kullanılır. `F = cholesky(A)` genellikle `F\b` ile denklemler sistemlerini çözmek için kullanılır, ancak [`diag`](@ref), [`det`](@ref) ve [`logdet`](@ref) gibi yöntemler de `F` için tanımlanmıştır. Ayrıca, `F`'den bireysel faktörler çıkartabilirsiniz, `F.L` kullanarak. Ancak, varsayılan olarak pivotlama açık olduğundan, faktörizasyon içsel olarak `A == P'*L*L'*P` şeklinde bir permütasyon matris `P` ile temsil edilir; sadece `L`'yi `P`'yi hesaba katmadan kullanmak yanlış sonuçlar verecektir. Permütasyon etkilerini dahil etmek için, genellikle `PtL = F.PtL` (eşdeğeri `P'*L`) ve `LtP = F.UP` (eşdeğeri `L'*P`) gibi "birleşik" faktörler çıkartmak tercih edilir.

`check = true` olduğunda, ayrıştırma başarısız olursa bir hata fırlatılır. `check = false` olduğunda, ayrıştırmanın geçerliliğini kontrol etme sorumluluğu ([`issuccess`](@ref) aracılığıyla) kullanıcıya aittir.

İsteğe bağlı `shift` anahtar argümanını ayarlamak, `A` yerine `A+shift*I`'nin faktörizasyonunu hesaplar. `perm` argümanı sağlanırsa, bu, kullanılacak sıralamayı veren `1:size(A,1)`'in bir permütasyonu olmalıdır (CHOLMOD'un varsayılan AMD sıralaması yerine).

# Örnekler

Aşağıdaki örnekte, kullanılan dolgu azaltıcı permütasyon `[3, 2, 1]`'dir. `perm` `1:3` olarak ayarlandığında, yani hiç permütasyon uygulanmadığında, faktördeki sıfırdan farklı eleman sayısı 6'dır.

```jldoctest
julia> A = [2 1 1; 1 2 0; 1 0 2]
3×3 Matrix{Int64}:
 2  1  1
 1  2  0
 1  0  2

julia> C = cholesky(sparse(A))
SparseArrays.CHOLMOD.Factor{Float64, Int64}
type:    LLt
method:  simplicial
maxnnz:  5
nnz:     5
success: true

julia> C.p
3-element Vector{Int64}:
 3
 2
 1

julia> L = sparse(C.L);

julia> Matrix(L)
3×3 Matrix{Float64}:
 1.41421   0.0       0.0
 0.0       1.41421   0.0
 0.707107  0.707107  1.0

julia> L * L' ≈ A[C.p, C.p]
true

julia> P = sparse(1:3, C.p, ones(3))
3×3 SparseMatrixCSC{Float64, Int64} with 3 stored entries:
  ⋅    ⋅   1.0
  ⋅   1.0   ⋅
 1.0   ⋅    ⋅

julia> P' * L * L' * P ≈ A
true

julia> C = cholesky(sparse(A), perm=1:3)
SparseArrays.CHOLMOD.Factor{Float64, Int64}
type:    LLt
method:  simplicial
maxnnz:  6
nnz:     6
success: true

julia> L = sparse(C.L);

julia> Matrix(L)
3×3 Matrix{Float64}:
 1.41421    0.0       0.0
 0.707107   1.22474   0.0
 0.707107  -0.408248  1.1547

julia> L * L' ≈ A
true
```

!!! not
    Bu yöntem, [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse) kütüphanesinden CHOLMOD[^ACM887][^DavisHager2009] kullanır. CHOLMOD yalnızca tek veya çift hassasiyette gerçek veya karmaşık türleri destekler. Bu element türlerinde olmayan giriş matrisleri uygun şekilde bu türlere dönüştürülecektir.

    CHOLMOD'dan birçok başka işlev sarılmıştır ancak `Base.SparseArrays.CHOLMOD` modülünden dışa aktarılmamıştır.


[^ACM887]: Chen, Y., Davis, T. A., Hager, W. W., & Rajamanickam, S. (2008). Algorithm 887: CHOLMOD, Supernodal Sparse Cholesky Factorization and Update/Downdate. ACM Trans. Math. Softw., 35(3). [doi:10.1145/1391989.1391995](https://doi.org/10.1145/1391989.1391995)

[^DavisHager2009]: Davis, Timothy A., & Hager, W. W. (2009). Dynamic Supernodes in Sparse Cholesky Update/Downdate and Triangular Solves. ACM Trans. Math. Softw., 35(4). [doi:10.1145/1462173.1462176](https://doi.org/10.1145/1462173.1462176)
