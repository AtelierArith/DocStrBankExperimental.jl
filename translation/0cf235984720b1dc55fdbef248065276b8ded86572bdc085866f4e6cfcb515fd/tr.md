```
ldlt(A::SparseMatrixCSC; shift = 0.0, check = true, perm=nothing) -> CHOLMOD.Factor
```

Sıkışık bir matris `A`'nın $LDL'$ faktorizasyonunu hesaplar. `A`, bir [`SparseMatrixCSC`](@ref) veya bir [`Symmetric`](@ref)/[`Hermitian`](@ref) görünümü olmalıdır. `A`'nın tür etiketi olmasa bile, hala simetrik veya Hermitian olmalıdır. Bir dolgu azaltıcı permütasyon kullanılır. `F = ldlt(A)` genellikle `A*x = b` denklemlerini `F\b` ile çözmek için kullanılır. Döndürülen faktorizasyon nesnesi `F`, ayrıca [`diag`](@ref), [`det`](@ref), [`logdet`](@ref) ve [`inv`](@ref) yöntemlerini de destekler. `F`'den bireysel faktörleri `F.L` kullanarak çıkarabilirsiniz. Ancak, varsayılan olarak pivotlama açık olduğundan, faktorizasyon içsel olarak `A == P'*L*D*L'*P` şeklinde temsil edilir; `P` ile hesaba katmadan sadece `L` kullanmak yanlış sonuçlar verecektir. Permütasyon etkilerini dahil etmek için, genellikle `PtL = F.PtL` (eşdeğeri `P'*L`) ve `LtP = F.UP` (eşdeğeri `L'*P`) gibi "birleşik" faktörleri çıkarmak tercih edilir. Desteklenen faktörlerin tam listesi `:L, :PtL, :D, :UP, :U, :LD, :DU, :PtLD, :DUP`'dir.

`check = true` olduğunda, ayrıştırma başarısız olursa bir hata fırlatılır. `check = false` olduğunda, ayrıştırmanın geçerliliğini kontrol etme sorumluluğu (via [`issuccess`](@ref)) kullanıcıya aittir.

İsteğe bağlı `shift` anahtar argümanını ayarlamak, `A` yerine `A+shift*I`'nin faktorizasyonunu hesaplar. `perm` argümanı sağlanırsa, bu, kullanılacak sıralamayı veren `1:size(A,1)`'in bir permütasyonu olmalıdır (CHOLMOD'un varsayılan AMD sıralaması yerine).

!!! not
    Bu yöntem, [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse) kütüphanesinden CHOLMOD[^ACM887][^DavisHager2009] kullanır. CHOLMOD yalnızca tekil veya çift hassasiyetli gerçek veya karmaşık türleri destekler. Bu eleman türlerinde olmayan giriş matrisleri, uygun şekilde bu türlere dönüştürülecektir.

    CHOLMOD'dan birçok başka işlev sarılmıştır ancak `Base.SparseArrays.CHOLMOD` modülünden dışa aktarılmamıştır.

