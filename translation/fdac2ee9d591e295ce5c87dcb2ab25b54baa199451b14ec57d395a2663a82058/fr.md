```
invmod(n::Integer, m::Integer)
```

Prenez l'inverse de `n` modulo `m` : `y` tel que $n y = 1 \pmod m$, et $div(y,m) = 0$. Cela générera une erreur si $m = 0$, ou si $gcd(n,m) \neq 1$.

# Exemples

```jldoctest
julia> invmod(2, 5)
3

julia> invmod(2, 3)
2

julia> invmod(5, 6)
5
```
