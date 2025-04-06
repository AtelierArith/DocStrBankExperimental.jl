```
diagm(v::AbstractVector)
diagm(m::Integer, n::Integer, v::AbstractVector)
```

Konstruiere eine Matrix mit den Elementen des Vektors als Diagonalelemente. Standardmäßig ist die Matrix quadratisch und ihre Größe wird durch `length(v)` angegeben, aber eine nicht-quadratische Größe `m`×`n` kann angegeben werden, indem `m,n` als die ersten Argumente übergeben werden.

# Beispiele

```jldoctest
julia> diagm([1,2,3])
3×3 Matrix{Int64}:
 1  0  0
 0  2  0
 0  0  3
```
