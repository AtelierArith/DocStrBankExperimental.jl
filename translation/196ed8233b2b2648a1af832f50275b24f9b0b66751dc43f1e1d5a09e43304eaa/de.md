```
typejoin(T, S, ...)
```

Gibt den nächsten gemeinsamen Vorfahren der Typen `T` und `S` zurück, d.h. den engsten Typ, von dem sie beide erben. Rekursiert über zusätzliche varargs.

# Beispiele

```jldoctest
julia> typejoin(Int, Float64)
Real

julia> typejoin(Int, Float64, ComplexF32)
Number
```
