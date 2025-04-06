```
binom(x::Number, k::Integer)
```

Genelleştirilmiş binom katsayısı, `k ≥ 0` için aşağıdaki polinom ile tanımlanır

$$
\frac{1}{k!} \prod_{j=0}^{k-1} (x - j)
$$

`k < 0` olduğunda sıfır döner.

Tam sayı `x` durumu için bu, sıradan tam sayı binom katsayısına eşdeğerdir

$$
\binom{n}{k} = \frac{n!}{k! (n-k)!}
$$

Tam olmayan `k` için daha fazla genelleme matematiksel olarak mümkündür, ancak Gamma fonksiyonu ve/veya beta fonksiyonu içerir; bu fonksiyonlar Julia standart kütüphanesinde sağlanmamaktadır, ancak [SpecialFunctions.jl](https://github.com/JuliaMath/SpecialFunctions.jl) gibi harici paketlerde mevcuttur.

# Harici bağlantılar

  * [Binom katsayısı](https://en.wikipedia.org/wiki/Binomial_coefficient) Vikipedi'de.
