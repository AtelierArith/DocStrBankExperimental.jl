```
cumprod(A; dims::Integer)
```

Kumulative Produkt entlang der Dimension `dim`. Siehe auch [`cumprod!`](@ref), um ein vorab zugewiesenes Ausgabearray zu verwenden, sowohl für die Leistung als auch um die Genauigkeit der Ausgabe zu steuern (z. B. um Überlauf zu vermeiden).

# Beispiele

```jldoctest
julia> a = Int8[1 2 3; 4 5 6];

julia> cumprod(a, dims=1)
2×3 Matrix{Int64}:
 1   2   3
 4  10  18

julia> cumprod(a, dims=2)
2×3 Matrix{Int64}:
 1   2    6
 4  20  120
```
