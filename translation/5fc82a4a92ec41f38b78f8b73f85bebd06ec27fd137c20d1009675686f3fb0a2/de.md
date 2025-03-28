```
eltype(type)
```

Bestimmen Sie den Typ der Elemente, die durch das Iterieren über eine Sammlung des angegebenen `type` erzeugt werden. Für Dictionary-Typen wird dies ein `Pair{KeyType,ValType}` sein. Die Definition `eltype(x) = eltype(typeof(x))` wird zur Verfügung gestellt, damit Instanzen anstelle von Typen übergeben werden können. Die Form, die ein Typ-Argument akzeptiert, sollte jedoch für neue Typen definiert werden.

Siehe auch: [`keytype`](@ref), [`typeof`](@ref).

# Beispiele

```jldoctest
julia> eltype(fill(1f0, (2,2)))
Float32

julia> eltype(fill(0x1, (2,2)))
UInt8
```
