```
svd(A; full::Bool = false, alg::Algorithm = default_svd_alg(A)) -> SVD
```

`A`'nın tekil değer ayrıştırmasını (SVD) hesaplayın ve bir `SVD` nesnesi döndürün.

`U`, `S`, `V` ve `Vt`, `F.U`, `F.S`, `F.V` ve `F.Vt` ile ayrıştırmadan elde edilebilir; böylece `A = U * Diagonal(S) * Vt`. Algoritma `Vt`'yi üretir ve bu nedenle `Vt`'yi çıkarmak `V`'den daha verimlidir. `S`'deki tekil değerler azalan sırada sıralanmıştır.

Ayrıştırmayı yineleyerek `U`, `S` ve `V` bileşenlerini elde edersiniz.

Eğer `full = false` (varsayılan), "ince" bir SVD döndürülür. $M \times N$ boyutundaki bir matris `A` için, tam ayrıştırmada `U` $M \times M$ ve `V` $N \times N$ iken, ince ayrıştırmada `U` $M \times K$ ve `V` $N \times K$'dır; burada $K = \min(M,N)$ tekil değerlerin sayısıdır.

Eğer `alg = DivideAndConquer()` ise SVD'yi hesaplamak için bir böl ve fethet algoritması kullanılır. Diğer bir (genellikle daha yavaş ama daha doğru) seçenek `alg = QRIteration()`'dır.

!!! compat "Julia 1.3"
    `alg` anahtar argümanı Julia 1.3 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> A = rand(4,3);

julia> F = svd(A); # Ayrıştırma Nesnesini Sakla

julia> A ≈ F.U * Diagonal(F.S) * F.Vt
true

julia> U, S, V = F; # yineleme ile parçalama

julia> A ≈ U * Diagonal(S) * V'
true

julia> Uonly, = svd(A); # Sadece U'yu Sakla

julia> Uonly == U
true
```
