```
QRCompactWY <: Factorization
```

Kompakt blok formatında saklanan bir QR matris faktorizasyonu, genellikle [`qr`](@ref) ile elde edilir. Eğer $A$ bir `m`×`n` matris ise, o zaman

$$
A = Q R
$$

burada $Q$ ortogonal/birleşik bir matris ve $R$ üst üçgen bir matristir. Bu, ortogonal/birleşik matris $Q$'nun *Kompakt WY* formatında saklandığı için [`QR`](@ref) formatına benzer [^Schreiber1989]. Blok boyutu $n_b$ için, `m`×`n` alt trapezoidal matris $V$ ve $b = \lceil \min(m,n) / n_b \rceil$ üst üçgen matrislerden oluşan bir matris $T = (T_1 \; T_2 \; ... \; T_{b-1} \; T_b')$ olarak saklanır; burada $T_j$ boyutu $n_b$×$n_b$ olan ($j = 1, ..., b-1$) ve üst trapezoidal $n_b$×$\min(m,n) - (b-1) n_b$ matris $T_b'$ ($j=b$) ile birlikte $T_b$ ile gösterilen üst kare kısmı ile birlikte

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T)
= \prod_{j=1}^{b} (I - V_j T_j V_j^T)
$$

şeklindedir; burada $v_i$ $V$'nin $i$'inci sütunu, $\tau_i$ ise `[diag(T_1); diag(T_2); …; diag(T_b)]`'nin $i$'inci elemanıdır ve $(V_1 \; V_2 \; ... \; V_b)$ $V$'nin sol `m`×`min(m, n)` bloğudur. [`qr`](@ref) kullanılarak oluşturulduğunda, blok boyutu $n_b = \min(m, n, 36)$ olarak verilir.

Ayrıştırmayı yinelemek `Q` ve `R` bileşenlerini üretir.

Nesne iki alana sahiptir:

  * `factors`, [`QR`](@ref) türünde olduğu gibi, bir `m`×`n` matristir.

      * Üst üçgen kısmı $R$'nin elemanlarını içerir, yani `R = triu(F.factors)` bir `QR` nesnesi `F` için.
      * Alt diyagonal kısmı, `V = I + tril(F.factors, -1)` şeklinde paketlenmiş formatta saklanan yansıtıcılar $v_i$'yi içerir.
  * `T`, yukarıda açıklandığı gibi bir $n_b$-çarpı-$\min(m,n)$ matristir. Her üçgen matris $T_j$ için alt diyagonal elemanlar göz ardı edilir.

!!! note
    Bu format, daha eski *WY* temsil biçimi ile karıştırılmamalıdır [^Bischof1987].


[^Bischof1987]: C Bischof ve C Van Loan, "The WY representation for products of Householder matrices", SIAM J Sci Stat Comput 8 (1987), s2-s13. [doi:10.1137/0908009](https://doi.org/10.1137/0908009)

[^Schreiber1989]: R Schreiber ve C Van Loan, "A storage-efficient WY representation for products of Householder transformations", SIAM J Sci Stat Comput 10 (1989), 53-57. [doi:10.1137/0910005](https://doi.org/10.1137/0910005)
