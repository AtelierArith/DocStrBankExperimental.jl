```
prod(f, A::AbstractArray; dims)
```

Multiplizieren Sie die Ergebnisse des Aufrufs der Funktion `f` für jedes Element eines Arrays über die angegebenen Dimensionen.

# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> prod(abs2, A, dims=1)
1×2 Matrix{Int64}:
 9  64

julia> prod(abs2, A, dims=2)
2×1 Matrix{Int64}:
   4
 144
```
