```
sum(f, A::AbstractArray; dims)
```

Summiere die Ergebnisse des Aufrufs der Funktion `f` auf jedes Element eines Arrays über die angegebenen Dimensionen.

# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> sum(abs2, A, dims=1)
1×2 Matrix{Int64}:
 10  20

julia> sum(abs2, A, dims=2)
2×1 Matrix{Int64}:
  5
 25
```
