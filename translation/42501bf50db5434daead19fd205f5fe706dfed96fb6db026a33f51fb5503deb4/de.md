```
isimmutable(v) -> Bool
```

!!! warning
    Erwägen Sie stattdessen die Verwendung von `!ismutable(v)`, da `isimmutable(v)` in einer zukünftigen Version durch `!ismutable(v)` ersetzt wird. (Seit Julia 1.5)


Gibt `true` zurück, wenn der Wert `v` unveränderlich ist. Siehe [Mutable Composite Types](@ref) für eine Diskussion über Unveränderlichkeit. Beachten Sie, dass diese Funktion auf Werten arbeitet, sodass sie Ihnen sagt, dass ein Wert von `DataType` veränderlich ist, wenn Sie ihr einen Typ geben.

# Beispiele

```jldoctest
julia> isimmutable(1)
true

julia> isimmutable([1,2])
false
```
