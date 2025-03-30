```
invmod(n::Integer, m::Integer)
```

`m` modülünde `n`'nin tersini alır: $n y = 1 \pmod m$ olacak şekilde `y`, ve $div(y,m) = 0$. Bu, $m = 0$ olduğunda veya $gcd(n,m) \neq 1$ olduğunda bir hata fırlatır.

# Örnekler

```jldoctest
julia> invmod(2, 5)
3

julia> invmod(2, 3)
2

julia> invmod(5, 6)
5
```
