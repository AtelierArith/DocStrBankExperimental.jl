```
nextprod(factors::Union{Tuple,AbstractVector}, n)
```

Entier suivant supérieur ou égal à `n` qui peut être écrit sous la forme $\prod k_i^{p_i}$ pour des entiers $p_1$, $p_2$, etc., pour les facteurs $k_i$ dans `factors`.

# Exemples

```jldoctest
julia> nextprod((2, 3), 105)
108

julia> 2^2 * 3^3
108
```

!!! compat "Julia 1.6"
    La méthode qui accepte un tuple nécessite Julia 1.6 ou une version ultérieure.

