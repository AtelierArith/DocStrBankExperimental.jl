```
sizeof(T::DataType)
sizeof(obj)
```

Größe in Bytes der kanonischen binären Darstellung des gegebenen `DataType` `T`, falls vorhanden. Oder die Größe in Bytes des Objekts `obj`, wenn es kein `DataType` ist.

Siehe auch [`Base.summarysize`](@ref).

# Beispiele

```jldoctest
julia> sizeof(Float32)
4

julia> sizeof(ComplexF64)
16

julia> sizeof(1.0)
8

julia> sizeof(collect(1.0:10.0))
80

julia> struct StructWithPadding
           x::Int64
           flag::Bool
       end

julia> sizeof(StructWithPadding) # nicht die Summe von `sizeof` der Felder aufgrund von Padding
16

julia> sizeof(Int64) + sizeof(Bool) # anders als oben
9
```

Wenn `DataType` `T` keine spezifische Größe hat, wird ein Fehler ausgelöst.

```jldoctest
julia> sizeof(AbstractArray)
ERROR: Abstrakte Typ AbstractArray hat keine bestimmte Größe.
Stacktrace:
[...]
```
