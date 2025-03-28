```
eigvals(A; permute::Bool=true, scale::Bool=true, sortby) -> values
```

Gibt die Eigenwerte von `A` zurück.

Für allgemeine nicht-symmetrische Matrizen ist es möglich, anzugeben, wie die Matrix vor der Berechnung der Eigenwerte ausgewogen werden soll. Die Schlüsselwörter `permute`, `scale` und `sortby` sind dieselben wie für [`eigen`](@ref).

# Beispiele

```jldoctest
julia> diag_matrix = [1 0; 0 4]
2×2 Matrix{Int64}:
 1  0
 0  4

julia> eigvals(diag_matrix)
2-element Vector{Float64}:
 1.0
 4.0
```
