```
powermod(x::Integer, p::Integer, m)
```

$$
x^p \pmod m
$$

를 계산합니다.

# 예제

```jldoctest
julia> powermod(2, 6, 5)
4

julia> mod(2^6, 5)
4

julia> powermod(5, 2, 20)
5

julia> powermod(5, 2, 19)
6

julia> powermod(5, 3, 19)
11
```
