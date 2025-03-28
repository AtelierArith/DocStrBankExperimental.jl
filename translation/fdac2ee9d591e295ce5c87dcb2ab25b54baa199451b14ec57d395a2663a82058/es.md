```
invmod(n::Integer, m::Integer)
```

Toma el inverso de `n` módulo `m`: `y` tal que $n y = 1 \pmod m$, y $div(y,m) = 0$. Esto lanzará un error si $m = 0$, o si $gcd(n,m) \neq 1$.

# Ejemplos

```jldoctest
julia> invmod(2, 5)
3

julia> invmod(2, 3)
2

julia> invmod(5, 6)
5
```
