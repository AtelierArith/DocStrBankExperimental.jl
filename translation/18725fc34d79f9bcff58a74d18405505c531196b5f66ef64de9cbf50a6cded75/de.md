```
view(A, inds...)
```

Wie [`getindex`](@ref), aber gibt ein leichtgewichtiges Array zurück, das faul auf das übergeordnete Array `A` an dem gegebenen Index oder den Indizes `inds` verweist (oder effektiv eine *Ansicht* darauf ist), anstatt Elemente sofort zu extrahieren oder eine kopierte Teilmenge zu erstellen. Der Aufruf von [`getindex`](@ref) oder [`setindex!`](@ref) auf dem zurückgegebenen Wert (oft ein [`SubArray`](@ref)) berechnet die Indizes, um das übergeordnete Array im laufenden Betrieb zuzugreifen oder zu ändern. Das Verhalten ist undefiniert, wenn die Form des übergeordneten Arrays nach dem Aufruf von `view` geändert wird, da es keine Grenzkontrolle für das übergeordnete Array gibt; z. B. kann es zu einem Segmentierungsfehler führen.

Einige unveränderliche übergeordnete Arrays (wie Bereiche) können in einigen Fällen einfach ein neues Array neu berechnen, anstatt ein `SubArray` zurückzugeben, wenn dies effizient ist und kompatible Semantiken bietet.

!!! compat "Julia 1.6"
    In Julia 1.6 oder später kann `view` auf einem `AbstractString` aufgerufen werden, was ein `SubString` zurückgibt.


# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> b = view(A, :, 1)
2-element view(::Matrix{Int64}, :, 1) mit eltype Int64:
 1
 3

julia> fill!(b, 0)
2-element view(::Matrix{Int64}, :, 1) mit eltype Int64:
 0
 0

julia> A # Beachte, A hat sich geändert, obwohl wir b modifiziert haben
2×2 Matrix{Int64}:
 0  2
 0  4

julia> view(2:5, 2:3) # gibt einen Bereich zurück, da der Typ unveränderlich ist
3:4
```
