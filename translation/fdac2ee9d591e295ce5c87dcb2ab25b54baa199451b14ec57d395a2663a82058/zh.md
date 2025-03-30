```
invmod(n::Integer, m::Integer)
```

取 `n` 在模 `m` 下的逆：`y` 使得 $n y = 1 \pmod m$，并且 $div(y,m) = 0$。如果 $m = 0$，或者 $gcd(n,m) \neq 1$，则会抛出错误。

# 示例

```jldoctest
julia> invmod(2, 5)
3

julia> invmod(2, 3)
2

julia> invmod(5, 6)
5
```
