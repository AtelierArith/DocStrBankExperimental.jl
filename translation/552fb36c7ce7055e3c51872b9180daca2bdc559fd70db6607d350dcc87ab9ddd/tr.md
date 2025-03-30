```
gcdx(a, b)
```

`a` ve `b`'nin en büyük ortak (pozitif) bölenini ve Bézout katsayılarını, yani $ua+vb = d = gcd(a, b)$ eşitliğini sağlayan tam sayı katsayıları `u` ve `v`'yi hesaplar. `gcdx(a, b)` $(d, u, v)$ döner.

Argümanlar tam sayılar ve rasyonel sayılar olabilir.

!!! compat "Julia 1.4"
    Rasyonel argümanlar Julia 1.4 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> gcdx(12, 42)
(6, -3, 1)

julia> gcdx(240, 46)
(2, -9, 47)
```

!!! note
    Bézout katsayıları *benzersiz* olarak tanımlanmamıştır. `gcdx`, genişletilmiş Öklid algoritmasıyla hesaplanan minimal Bézout katsayılarını döner. (Ref: D. Knuth, TAoCP, 2/e, s. 325, Algoritma X.) İşaretli tam sayılar için, bu katsayılar `u` ve `v`, $|u| < |b/d|$ ve $|v| < |a/d|$ anlamında minimaldir. Ayrıca, `d` pozitif olacak şekilde `u` ve `v`'nin işaretleri seçilir. İşaretsiz tam sayılar için, katsayılar `u` ve `v` `typemax`'lerine yakın olabilir ve bu durumda kimlik yalnızca işaretsiz tam sayıların modüler aritmetiği aracılığıyla geçerlidir.

