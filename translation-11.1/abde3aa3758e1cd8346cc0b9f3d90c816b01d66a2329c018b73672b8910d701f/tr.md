```
lu(A::AbstractSparseMatrixCSC; check = true, q = nothing, control = get_umfpack_control()) -> F::UmfpackLU
```

Seyrek bir matris `A`'nın LU faktorizasyonunu hesaplayın.

Gerçek veya karmaşık eleman türüne sahip seyrek `A` için, `F`'nin dönüş türü `UmfpackLU{Tv, Ti}`'dir; burada `Tv` = [`Float64`](@ref) veya `ComplexF64` ve `Ti` bir tam sayı türüdür ([`Int32`](@ref) veya [`Int64`](@ref)).

`check = true` olduğunda, ayrıştırma başarısız olursa bir hata fırlatılır. `check = false` olduğunda, ayrıştırmanın geçerliliğini kontrol etme sorumluluğu ([`issuccess`](@ref) aracılığıyla) kullanıcıya aittir.

Permütasyon `q` ya bir permütasyon vektörü ya da `nothing` olabilir. Eğer hiçbir permütasyon vektörü sağlanmamışsa veya `q` `nothing` ise, UMFPACK'in varsayılanı kullanılır. Eğer permütasyon sıfır tabanlı değilse, sıfır tabanlı bir kopya yapılır.

`control` vektörü, Julia SparseArrays paketinin UMFPACK için varsayılan yapılandırmasına (Not: bu, iteratif iyileştirmeyi devre dışı bırakmak için UMFPACK varsayılanlarından değiştirilmiştir) varsayılan olarak ayarlanmıştır, ancak `UMFPACK_CONTROL` uzunluğunda bir vektör geçirerek değiştirilebilir; olası yapılandırmalar için UMFPACK kılavuzuna bakın. Örneğin, iteratif iyileştirmeyi yeniden etkinleştirmek için:

```
umfpack_control = SparseArrays.UMFPACK.get_umfpack_control(Float64, Int64) # Float64 seyrek matris için Julia varsayılan yapılandırmasını oku
SparseArrays.UMFPACK.show_umf_ctrl(umfpack_control) # isteğe bağlı - değerleri göster
umfpack_control[SparseArrays.UMFPACK.JL_UMFPACK_IRSTEP] = 2.0 # iteratif iyileştirmeyi yeniden etkinleştir (2, UMFPACK varsayılan maksimum iteratif iyileştirme adımıdır)

Alu = lu(A; control = umfpack_control)
x = Alu \ b   # Ax = b'yi çöz, UMFPACK iteratif iyileştirmesini de dahil et
```

Faktorizasyonun `F` bireysel bileşenlerine indeksleme ile erişilebilir:

| Bileşen | Açıklama                           |
|:------- |:---------------------------------- |
| `L`     | `LU`'nun `L` (alt üçgen) kısmı     |
| `U`     | `LU`'nun `U` (üst üçgen) kısmı     |
| `p`     | sağ permütasyon `Vector`           |
| `q`     | sol permütasyon `Vector`           |
| `Rs`    | ölçekleme faktörlerinin `Vector`'ı |
| `:`     | `(L,U,p,q,Rs)` bileşenleri         |

`F` ile `A` arasındaki ilişki

`F.L*F.U == (F.Rs .* A)[F.p, F.q]`

`F` ayrıca aşağıdaki işlevleri destekler:

  * [`\`](@ref)
  * [`det`](@ref)

Ayrıca [`lu!`](@ref) ile de bakın.

!!! not
    `lu(A::AbstractSparseMatrixCSC)` [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse) parçası olan UMFPACK[^ACM832] kütüphanesini kullanır. Bu kütüphane yalnızca [`Float64`](@ref) veya `ComplexF64` elemanlarına sahip seyrek matrisleri desteklediğinden, `lu` `A`'yı uygun şekilde `SparseMatrixCSC{Float64}` veya `SparseMatrixCSC{ComplexF64}` türünde bir kopyaya dönüştürür.


[^ACM832]: Davis, Timothy A. (2004b). Algoritma 832: UMFPACK V4.3–-bir Asimetrik Desenli Çoklu Yüzey Yöntemi. ACM Trans. Math. Softw., 30(2), 196–199. [doi:10.1145/992200.992206](https://doi.org/10.1145/992200.992206)
