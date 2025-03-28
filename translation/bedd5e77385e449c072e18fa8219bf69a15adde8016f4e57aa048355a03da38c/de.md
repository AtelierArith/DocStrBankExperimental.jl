```
product(iters...)
```

Gibt einen Iterator über das Produkt mehrerer Iteratoren zurück. Jedes erzeugte Element ist ein Tupel, dessen `i`-tes Element aus dem `i`-ten Argument-Iterator stammt. Der erste Iterator ändert sich am schnellsten.

Siehe auch: [`zip`](@ref), [`Iterators.flatten`](@ref).

# Beispiele

```jldoctest
julia> collect(Iterators.product(1:2, 3:5))
2×3 Matrix{Tuple{Int64, Int64}}:
 (1, 3)  (1, 4)  (1, 5)
 (2, 3)  (2, 4)  (2, 5)

julia> ans == [(x,y) for x in 1:2, y in 3:5]  # sammelt einen Generator, der Iterators.product verwendet
true
```
