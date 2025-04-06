```
similar(array, [element_type=eltype(array)], [dims=size(array)])
```

Erstellt ein nicht initialisiertes veränderliches Array mit dem angegebenen Elementtyp und der Größe, basierend auf dem gegebenen Quell-Array. Die zweiten und dritten Argumente sind beide optional und standardmäßig auf den `eltype` und die `size` des gegebenen Arrays gesetzt. Die Dimensionen können entweder als einzelnes Tupel-Argument oder als eine Reihe von Ganzzahl-Argumenten angegeben werden.

Benutzerdefinierte AbstractArray-Subtypen können wählen, welcher spezifische Array-Typ am besten geeignet ist, um den gegebenen Elementtyp und die Dimensionalität zurückzugeben. Wenn sie diese Methode nicht spezialisieren, ist der Standard ein `Array{element_type}(undef, dims...)`.

Zum Beispiel gibt `similar(1:10, 1, 4)` ein nicht initialisiertes `Array{Int,2}` zurück, da Bereiche weder veränderlich sind noch 2 Dimensionen unterstützen:

```julia-repl
julia> similar(1:10, 1, 4)
1×4 Matrix{Int64}:
 4419743872  4374413872  4419743888  0
```

Umgekehrt gibt `similar(trues(10,10), 2)` ein nicht initialisiertes `BitVector` mit zwei Elementen zurück, da `BitArray`s sowohl veränderlich sind als auch 1-dimensionale Arrays unterstützen können:

```julia-repl
julia> similar(trues(10,10), 2)
2-element BitVector:
 0
 0
```

Da `BitArray`s jedoch nur Elemente des Typs [`Bool`](@ref) speichern können, wird ein reguläres `Array` erstellt, wenn Sie einen anderen Elementtyp anfordern:

```julia-repl
julia> similar(falses(10), Float64, 2, 4)
2×4 Matrix{Float64}:
 2.18425e-314  2.18425e-314  2.18425e-314  2.18425e-314
 2.18425e-314  2.18425e-314  2.18425e-314  2.18425e-314
```

Siehe auch: [`undef`](@ref), [`isassigned`](@ref).
