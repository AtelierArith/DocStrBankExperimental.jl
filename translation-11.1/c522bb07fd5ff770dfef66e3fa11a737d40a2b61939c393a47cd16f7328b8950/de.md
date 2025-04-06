```
one(x)
one(T::type)
```

Gibt eine multiplikative Identität für `x` zurück: einen Wert, so dass `one(x)*x == x*one(x) == x`. Alternativ kann `one(T)` einen Typ `T` annehmen, in diesem Fall gibt `one` eine multiplikative Identität für jedes `x` vom Typ `T` zurück.

Wenn möglich, gibt `one(x)` einen Wert des gleichen Typs wie `x` zurück, und `one(T)` gibt einen Wert vom Typ `T` zurück. Dies ist jedoch möglicherweise nicht der Fall für Typen, die dimensionale Größen darstellen (z. B. Zeit in Tagen), da die multiplikative Identität dimensionslos sein muss. In diesem Fall sollte `one(x)` einen Identitätswert mit der gleichen Präzision (und Form, für Matrizen) wie `x` zurückgeben.

Wenn Sie eine Größe möchten, die vom gleichen Typ wie `x` oder vom Typ `T` ist, selbst wenn `x` dimensionale Größen hat, verwenden Sie stattdessen [`oneunit`](@ref).

Siehe auch die [`identity`](@ref) Funktion und `I` in [`LinearAlgebra`](@ref man-linalg) für die Identitätsmatrix.

# Beispiele

```jldoctest
julia> one(3.7)
1.0

julia> one(Int)
1

julia> import Dates; one(Dates.Day(1))
1
```
