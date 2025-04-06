```
@evalpoly(z, c...)
```

Polinomun $\sum_k z^{k-1} c[k]$ değerini `c[1]`, `c[2]`, ... için hesaplar; yani, katsayılar `z`'nin kuvvetine göre artan sırada verilmiştir. Bu makro, ya Horner yöntemi ya da karmaşık `z` için daha verimli bir Goertzel benzeri algoritma kullanan verimli satır içi koda genişler.

Ayrıca [`evalpoly`](@ref) bakınız.

# Örnekler

```jldoctest
julia> @evalpoly(3, 1, 0, 1)
10

julia> @evalpoly(2, 1, 0, 1)
5

julia> @evalpoly(2, 1, 1, 1)
7
```
