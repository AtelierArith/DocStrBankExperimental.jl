```
invmod(n::Integer, m::Integer)
```

`m`로 모듈로 `n`의 역수를 취합니다: $n y = 1 \pmod m$인 $y$와 $div(y,m) = 0$입니다. $m = 0$이거나 $gcd(n,m) \neq 1$인 경우 오류가 발생합니다.

# 예제

```jldoctest
julia> invmod(2, 5)
3

julia> invmod(2, 3)
2

julia> invmod(5, 6)
5
```
