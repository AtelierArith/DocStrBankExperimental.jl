```
invmod(n::Integer, m::Integer)
```

Nehmen Sie das Inverse von `n` modulo `m`: `y`, so dass $n y = 1 \pmod m$, und $div(y,m) = 0$. Dies wird einen Fehler auslösen, wenn $m = 0$ oder wenn $gcd(n,m) \neq 1$.

# Beispiele

```jldoctest
julia> invmod(2, 5)
3

julia> invmod(2, 3)
2

julia> invmod(5, 6)
5
```
