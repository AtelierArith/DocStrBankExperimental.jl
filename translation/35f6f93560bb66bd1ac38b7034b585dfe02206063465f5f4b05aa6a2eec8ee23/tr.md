```
evalpoly(x, p)
```

Polinomun $\sum_k x^{k-1} p[k]$ değerini hesaplar; yani, katsayılar `p[1]`, `p[2]`, ... şeklinde `x`'in kuvvetine göre artan sırada verilmiştir. Katsayıların sayısı statik olarak biliniyorsa, yani `p` bir `Tuple` ise döngüler derleme zamanında açılır. Bu fonksiyon, `x` gerçekse Horner yöntemi kullanarak verimli kod üretir veya `x` karmaşık ise Goertzel benzeri [^DK62] algoritmasını kullanır.

[^DK62]: Donald Knuth, Art of Computer Programming, Volume 2: Seminumerical Algorithms, Sec. 4.6.4.

!!! compat "Julia 1.4"
    Bu fonksiyon Julia 1.4 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> evalpoly(2, (1, 2, 3))
17
```
