```
QRPivoted <: Factorization
```

Sütun pivotlamalı bir QR matris faktorizasyonu, genellikle [`qr`](@ref) ile elde edilen paketlenmiş bir formatta. Eğer $A$ bir `m`×`n` matris ise, o zaman

$$
A P = Q R
$$

burada $P$ bir permütasyon matrisidir, $Q$ ortogonal/birleşik bir matris ve $R$ üst üçgen bir matristir. Matris $Q$, bir dizi Householder yansıtıcısı olarak saklanır:

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T).
$$

Ayrıştırmayı yineleyerek `Q`, `R` ve `p` bileşenlerini üretir.

Nesne üç alana sahiptir:

  * `factors`, `m`×`n` boyutunda bir matristir.

      * Üst üçgen kısmı $R$'nin elemanlarını içerir, yani `R = triu(F.factors)` bir `QR` nesnesi `F` için.
      * Alt diyagonal kısmı, $v_i$'lerin yansıtıcılarını içerir ve bunlar, $v_i$'nin matris `V = I + tril(F.factors, -1)`'nin $i$'inci sütunu olduğu paketlenmiş bir formatta saklanır.
  * `τ`, $au_i$ katsayılarını içeren `min(m,n)` uzunluğunda bir vektördür.
  * `jpvt`, permütasyon $P$'ye karşılık gelen `n` uzunluğunda bir tam sayı vektörüdür.
