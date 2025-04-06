```
reinterpret(T::DataType, A::AbstractArray)
```

Konstruiere eine Ansicht des Arrays mit denselben binären Daten wie das gegebene Array, jedoch mit `T` als Elementtyp.

Diese Funktion funktioniert auch bei "faulen" Arrays, deren Elemente nicht berechnet werden, bis sie explizit abgerufen werden. Zum Beispiel funktioniert `reinterpret` auf dem Bereich `1:6` ähnlich wie auf dem dichten Vektor `collect(1:6)`:

```jldoctest
julia> reinterpret(Float32, UInt32[1 2 3 4 5])
1×5 reinterpret(Float32, ::Matrix{UInt32}):
 1.0f-45  3.0f-45  4.0f-45  6.0f-45  7.0f-45

julia> reinterpret(Complex{Int}, 1:6)
3-element reinterpret(Complex{Int64}, ::UnitRange{Int64}):
 1 + 2im
 3 + 4im
 5 + 6im
```

Wenn die Position der Padding-Bits zwischen `T` und `eltype(A)` nicht übereinstimmt, wird das resultierende Array schreibgeschützt oder leseschreibgeschützt sein, um zu verhindern, dass ungültige Bits geschrieben oder gelesen werden.

```jldoctest
julia> a = reinterpret(Tuple{UInt8, UInt32}, UInt32[1, 2])
1-element reinterpret(Tuple{UInt8, UInt32}, ::Vector{UInt32}):
 (0x01, 0x00000002)

julia> a[1] = 3
ERROR: Padding des Typs Tuple{UInt8, UInt32} ist nicht kompatibel mit dem Typ UInt32.

julia> b = reinterpret(UInt32, Tuple{UInt8, UInt32}[(0x01, 0x00000002)]); # anzeigen wird einen Fehler verursachen

julia> b[1]
ERROR: Padding des Typs UInt32 ist nicht kompatibel mit dem Typ Tuple{UInt8, UInt32}.
```
