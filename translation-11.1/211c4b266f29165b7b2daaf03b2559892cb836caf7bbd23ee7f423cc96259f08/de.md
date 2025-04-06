```
elsize(type)
```

Berechne den Speicherabstand in Bytes zwischen aufeinanderfolgenden Elementen des [`eltype`](@ref), die im angegebenen `type` gespeichert sind, wenn die Array-Elemente dicht mit einem einheitlichen linearen Abstand gespeichert sind.

# Beispiele

```jldoctest
julia> Base.elsize(rand(Float32, 10))
4
```
