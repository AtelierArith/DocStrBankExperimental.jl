```
lu!(F::UmfpackLU, A::AbstractSparseMatrixCSC; check=true, reuse_symbolic=true, q=nothing) -> F::UmfpackLU
```

Seyrek bir matris `A`'nın LU faktorizasyonunu hesaplayın, zaten mevcut olan `F`'de saklanan sembolik faktorizasyonu yeniden kullanarak. `reuse_symbolic` false olarak ayarlanmadığı sürece, seyrek matris `A`'nın, LU faktorizasyonu `F`'yi oluşturmak için kullanılan matrisle aynı sıfır dışı desenine sahip olması gerekir, aksi takdirde bir hata fırlatılır. `A` ve `F`'nin boyutları farklıysa, tüm vektörler buna göre yeniden boyutlandırılacaktır.

`check = true` olduğunda, ayrıştırma başarısız olursa bir hata fırlatılır. `check = false` olduğunda, ayrıştırmanın geçerliliğini kontrol etme sorumluluğu (via [`issuccess`](@ref)) kullanıcıya aittir.

Permütasyon `q` ya bir permütasyon vektörü ya da `nothing` olabilir. Eğer hiçbir permütasyon vektörü sağlanmazsa veya `q` `nothing` ise, UMFPACK'in varsayılanı kullanılır. Eğer permütasyon sıfır tabanlı değilse, sıfır tabanlı bir kopya oluşturulur.

Ayrıca bkz. [`lu`](@ref)

!!! not
    `lu!(F::UmfpackLU, A::AbstractSparseMatrixCSC)` SuiteSparse'in bir parçası olan UMFPACK kütüphanesini kullanır. Bu kütüphane yalnızca [`Float64`](@ref) veya `ComplexF64` elemanlarına sahip seyrek matrisleri desteklediğinden, `lu!` otomatik olarak türleri LU faktorizasyonu tarafından belirlenen veya uygun olduğunda `SparseMatrixCSC{ComplexF64}` olarak dönüştürecektir.


!!! uyumluluk "Julia 1.5"
    `UmfpackLU` için `lu!` en az Julia 1.5 gerektirir.


# Örnekler

```jldoctest
julia> A = sparse(Float64[1.0 2.0; 0.0 3.0]);

julia> F = lu(A);

julia> B = sparse(Float64[1.0 1.0; 0.0 1.0]);

julia> lu!(F, B);

julia> F \ ones(2)
2-element Vector{Float64}:
 0.0
 1.0
```
