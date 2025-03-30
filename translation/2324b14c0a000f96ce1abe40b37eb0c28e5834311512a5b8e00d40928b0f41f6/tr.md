```
QR <: Factorization
```

Bir QR matris faktorizasyonu, genellikle [`qr`](@ref) ile elde edilen, paketlenmiş bir formatta saklanır. Eğer $A$ bir `m`×`n` matris ise, o zaman

$$
A = Q R
$$

burada $Q$ ortogonal/birleşik bir matris ve $R$ üst üçgen matristir. Matris $Q$, aşağıdaki gibi Householder yansıtıcılarının $v_i$ ve katsayılarının $\tau_i$ bir dizisi olarak saklanır:

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T).
$$

Ayrıştırmayı yineleyerek `Q` ve `R` bileşenlerini üretiriz.

Nesne iki alana sahiptir:

  * `factors`, `m`×`n` boyutunda bir matristir.

      * Üst üçgen kısmı $R$'nin elemanlarını içerir, yani `R = triu(F.factors)` bir `QR` nesnesi `F` için.
      * Alt diyagonal kısmı, $v_i$'lerin paketlenmiş formatta saklandığı, `V = I + tril(F.factors, -1)` matrisinin $i$'nci sütunu olan yansıtıcıları içerir.
  * `τ`, $au_i$ katsayılarını içeren `min(m,n)` uzunluğunda bir vektördür.
