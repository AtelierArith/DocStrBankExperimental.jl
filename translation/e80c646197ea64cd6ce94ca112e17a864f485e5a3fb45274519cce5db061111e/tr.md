```
lcm(x, y...)
```

En küçük (pozitif) çarpan (veya herhangi bir argüman sıfırsa sıfır). Argümanlar tam sayılar ve rasyonel sayılar olabilir.

!!! uyumluluk "Julia 1.4"
    Rasyonel argümanlar Julia 1.4 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> lcm(2, 3)
6

julia> lcm(-2, 3)
6

julia> lcm(0, 3)
0

julia> lcm(0, 0)
0

julia> lcm(1//3, 2//3)
2//3

julia> lcm(1//3, -2//3)
2//3

julia> lcm(1//3, 2)
2//1

julia> lcm(1, 3, 5, 7)
105
```
