```
oneunit(x::T)
oneunit(T::Type)
```

Gibt `T(one(x))` zurück, wobei `T` entweder der Typ des Arguments oder (wenn ein Typ übergeben wird) das Argument ist. Dies unterscheidet sich von [`one`](@ref) für dimensionale Größen: `one` ist dimensionslos (eine multiplikative Identität), während `oneunit` dimensional ist (vom gleichen Typ wie `x` oder vom Typ `T`).

# Beispiele

```jldoctest
julia> oneunit(3.7)
1.0

julia> import Dates; oneunit(Dates.Day)
1 Tag
```
