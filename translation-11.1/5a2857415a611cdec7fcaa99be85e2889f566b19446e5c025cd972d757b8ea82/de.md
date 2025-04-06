```
spzeros([typ,]m[,n])
```

Erstellt einen spärlichen Vektor der Länge `m` oder eine spärliche Matrix der Größe `m x n`. Dieses spärliche Array wird keine Nicht-Null-Werte enthalten. Es wird während der Konstruktion kein Speicher für Nicht-Null-Werte reserviert. Der Typ ist standardmäßig [`Float64`](@ref), wenn nicht angegeben.

# Beispiele

```jldoctest
julia> spzeros(3, 3)
3×3 SparseMatrixCSC{Float64, Int64} mit 0 gespeicherten Einträgen:
  ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅

julia> spzeros(Float32, 4)
4-element SparseVector{Float32, Int64} mit 0 gespeicherten Einträgen
```
