```
cumsum(A; dims::Integer)
```

Kumulative Summe entlang der Dimension `dims`. Siehe auch [`cumsum!`](@ref), um ein vorab zugewiesenes Ausgabearray zu verwenden, sowohl für die Leistung als auch um die Genauigkeit der Ausgabe zu steuern (z. B. um Überlauf zu vermeiden).

# Beispiele

```jldoctest
julia> a = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> cumsum(a, dims=1)
2×3 Matrix{Int64}:
 1  2  3
 5  7  9

julia> cumsum(a, dims=2)
2×3 Matrix{Int64}:
 1  3   6
 4  9  15
```

!!! Hinweis     Der `eltype` des Rückgabearrays ist `Int` für vorzeichenbehaftete Ganzzahlen mit weniger als der Systemwortgröße und `UInt` für vorzeichenlose Ganzzahlen mit weniger als der Systemwortgröße. Um den `eltype` von Arrays mit kleinen vorzeichenbehafteten oder vorzeichenlosen Ganzzahlen zu erhalten, sollte `accumulate(+, A)` verwendet werden.

````
```jldoctest
julia> cumsum(Int8[100, 28])
2-element Vector{Int64}:
 100
 128

julia> accumulate(+,Int8[100, 28])
2-element Vector{Int8}:
  100
 -128
```

Im ersten Fall werden die Ganzzahlen auf die Systemwortgröße erweitert, und daher ist das Ergebnis `Int64[100, 128]`. Im letzteren Fall erfolgt keine solche Erweiterung, und der Ganzzahlüberlauf führt zu `Int8[100, -128]`.
````
