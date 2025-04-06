```
binomial(n::Integer, k::Integer)
```

*binom katsayısı* $\binom{n}{k}$, $(1+x)^n$ polinom genişlemesindeki $k$'inci terimin katsayısıdır.

Eğer $n$ negatif değilse, o zaman `k`'yı `n` öğesinden seçmenin yollarının sayısıdır:

$$
\binom{n}{k} = \frac{n!}{k! (n-k)!}
$$

burada $n!$ [`factorial`](@ref) fonksiyonudur.

Eğer $n$ negatifse, o zaman tanım şu kimlik ile yapılır:

$$
\binom{n}{k} = (-1)^k \binom{k-n-1}{k}
$$

Ayrıca bkz. [`factorial`](@ref).

# Örnekler

```jldoctest
julia> binomial(5, 3)
10

julia> factorial(5) ÷ (factorial(5-3) * factorial(3))
10

julia> binomial(-5, 3)
-35
```

# Dış bağlantılar

  * [Binom katsayısı](https://en.wikipedia.org/wiki/Binomial_coefficient) Wikipedia'da.

```
