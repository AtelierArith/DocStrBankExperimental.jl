```
qr(A, pivot = NoPivot(); blocksize) -> F
```

Matris `A`'nın QR faktorizasyonunu hesaplar: ortogonal (veya `A` karmaşık değerli ise ünite) bir matris `Q` ve

$$
A = Q R
$$

şeklinde bir üst üçgen matris `R` döner.

Dönen nesne `F`, faktorizasyonu paketlenmiş bir formatta saklar:

  * `pivot == ColumnNorm()` ise `F` bir [`QRPivoted`](@ref) nesnesidir,
  * A'nın eleman türü bir BLAS türü ([`Float32`](@ref), [`Float64`](@ref), `ComplexF32` veya `ComplexF64`) ise, `F` bir [`QRCompactWY`](@ref) nesnesidir,
  * aksi takdirde `F` bir [`QR`](@ref) nesnesidir.

Faktorizasyonun bireysel bileşenleri `F` üzerinden özellik erişimcileri ile alınabilir:

  * `F.Q`: ortogonal/ünite matris `Q`
  * `F.R`: üst üçgen matris `R`
  * `F.p`: pivotun permütasyon vektörü ([`QRPivoted`](@ref) yalnızca)
  * `F.P`: pivotun permütasyon matris ([`QRPivoted`](@ref) yalnızca)

!!! not
    `F.R` üzerinden üst üçgen faktöre yapılan her referans yeni bir dizi ayırır. Bu nedenle, o diziyi önbelleğe almak, örneğin `R = F.R` ile devam etmek tavsiye edilir.


Faktorizasyonu yineleyerek `Q`, `R` ve mevcutsa `p` bileşenlerini üretir.

`QR` nesneleri için aşağıdaki fonksiyonlar mevcuttur: [`inv`](@ref), [`size`](@ref) ve [`\`](@ref). `A` dikdörtgen olduğunda, `\` en küçük kareler çözümünü döner ve çözüm benzersiz değilse, en küçük norm olanı döner. `A` tam sıralı değilse, minimum norm çözümünü elde etmek için (sütun) pivotlama ile faktorizasyon gereklidir.

Tam/kare veya tam olmayan/kare `Q` ile çarpma mümkündür, yani hem `F.Q*F.R` hem de `F.Q*A` desteklenir. Bir `Q` matrisini [`Matrix`](@ref) ile normal bir matrise dönüştürebilirsiniz. Bu işlem "ince" Q faktörünü döner, yani `A` `m`×`n` ise ve `m>=n` ise, `Matrix(F.Q)` ortonormal sütunlara sahip bir `m`×`n` matris döner. "Tam" Q faktörünü almak için, bir `m`×`m` ortogonal matris, `F.Q*I` veya `collect(F.Q)` kullanın. Eğer `m<=n` ise, `Matrix(F.Q)` bir `m`×`m` ortogonal matris döner.

QR faktorizasyonu için blok boyutu, `pivot == NoPivot()` ve `A isa StridedMatrix{<:BlasFloat}` olduğunda anahtar argüman `blocksize :: Integer` ile belirtilebilir. `blocksize > minimum(size(A))` olduğunda göz ardı edilir. [`QRCompactWY`](@ref) için bakınız.

!!! uyumluluk "Julia 1.4"
    `blocksize` anahtar argümanı Julia 1.4 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> A = [3.0 -6.0; 4.0 -8.0; 0.0 1.0]
3×2 Matrix{Float64}:
 3.0  -6.0
 4.0  -8.0
 0.0   1.0

julia> F = qr(A)
LinearAlgebra.QRCompactWY{Float64, Matrix{Float64}, Matrix{Float64}}
Q faktörü: 3×3 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}
R faktörü:
2×2 Matrix{Float64}:
 -5.0  10.0
  0.0  -1.0

julia> F.Q * F.R == A
true
```

!!! not
    `qr` birden fazla tür döner çünkü LAPACK, Householder temel yansıtıcılarının ürünlerinin bellek depolama gereksinimlerini en aza indiren birkaç temsil kullanır, böylece `Q` ve `R` matrisleri ayrı yoğun matrisler olarak saklanabilir.

