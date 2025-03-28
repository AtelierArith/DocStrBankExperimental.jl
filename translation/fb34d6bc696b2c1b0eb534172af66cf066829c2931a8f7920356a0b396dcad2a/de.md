```
eachindex(A...)
eachindex(::IndexStyle, A::AbstractArray...)
```

Erstellen Sie ein iterierbares Objekt, um jeden Index eines `AbstractArray` `A` effizient zu besuchen. Für Array-Typen, die sich für schnelles lineares Indizieren entschieden haben (wie `Array`), ist dies einfach der Bereich `1:length(A)`, wenn sie 1-basiertes Indizieren verwenden. Für Array-Typen, die sich nicht für schnelles lineares Indizieren entschieden haben, wird typischerweise ein spezialisiertes kartesisches Intervall zurückgegeben, um effizient in das Array mit für jede Dimension angegebenen Indizes zu indizieren.

Im Allgemeinen akzeptiert `eachindex` beliebige Iterables, einschließlich Strings und Dictionaries, und gibt ein Iterator-Objekt zurück, das beliebige Indextypen unterstützt (z. B. ungleichmäßig verteilte oder nicht-ganzzahlige Indizes).

Wenn `A` ein `AbstractArray` ist, ist es möglich, den Stil der Indizes, die von `eachindex` zurückgegeben werden sollen, explizit anzugeben, indem ein Wert vom Typ `IndexStyle` als erstes Argument übergeben wird (typischerweise `IndexLinear()`, wenn lineare Indizes erforderlich sind, oder `IndexCartesian()`, wenn ein kartesisches Intervall gewünscht ist).

Wenn Sie mehr als ein `AbstractArray`-Argument übergeben, erstellt `eachindex` ein iterierbares Objekt, das für alle Argumente schnell ist (typischerweise ein [`UnitRange`](@ref), wenn alle Eingaben schnelles lineares Indizieren haben, andernfalls ein [`CartesianIndices`](@ref)). Wenn die Arrays unterschiedliche Größen und/oder Dimensionen haben, wird eine `DimensionMismatch`-Ausnahme ausgelöst.

Siehe auch [`pairs`](@ref)`(A)`, um über Indizes und Werte zusammen zu iterieren, und [`axes`](@ref)`(A, 2)`, um gültige Indizes entlang einer Dimension zu erhalten.

# Beispiele

```jldoctest
julia> A = [10 20; 30 40];

julia> for i in eachindex(A) # lineares Indizieren
           println("A[", i, "] == ", A[i])
       end
A[1] == 10
A[2] == 30
A[3] == 20
A[4] == 40

julia> for i in eachindex(view(A, 1:2, 1:1)) # kartesisches Indizieren
           println(i)
       end
CartesianIndex(1, 1)
CartesianIndex(2, 1)
```
