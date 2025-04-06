```
gcd(x, y...)
```

En büyük ortak (pozitif) bölen (veya tüm argümanlar sıfırsa sıfır). Argümanlar tam sayılar ve rasyonel sayılar olabilir.

!!! compat "Julia 1.4"
    Rasyonel argümanlar Julia 1.4 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> gcd(6, 9)
3

julia> gcd(6, -9)
3

julia> gcd(6, 0)
6

julia> gcd(0, 0)
0

julia> gcd(1//3, 2//3)
1//3

julia> gcd(1//3, -2//3)
1//3

julia> gcd(1//3, 2)
1//3

julia> gcd(0, 0, 10, 15)
5
```
