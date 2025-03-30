```
syconv!(uplo, A, ipiv) -> (A, work)
```

Bir simetrik matris `A`'yı (üçgen bir matris haline getirilmiş) iki matris `L` ve `D`'ye dönüştürür. Eğer `uplo = U` ise, `A` üst üçgendir. Eğer `uplo = L` ise, alt üçgendir. `ipiv`, üçgen faktorizasyondan elde edilen pivot vektörüdür. `A`, `L` ve `D` ile üzerine yazılır.
