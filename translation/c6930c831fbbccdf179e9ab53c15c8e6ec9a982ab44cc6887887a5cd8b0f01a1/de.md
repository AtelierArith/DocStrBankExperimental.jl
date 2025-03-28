```
nextprod(factors::Union{Tuple,AbstractVector}, n)
```

Nächste ganze Zahl größer oder gleich `n`, die als $\prod k_i^{p_i}$ für ganze Zahlen $p_1$, $p_2$, usw. geschrieben werden kann, für Faktoren $k_i$ in `factors`.

# Beispiele

```jldoctest
julia> nextprod((2, 3), 105)
108

julia> 2^2 * 3^3
108
```

!!! compat "Julia 1.6"
    Die Methode, die ein Tuple akzeptiert, erfordert Julia 1.6 oder höher.

