```
ismutable(v) -> Bool
```

Gibt `true` zurück, wenn und nur wenn der Wert `v` veränderlich ist. Siehe [Mutable Composite Types](@ref) für eine Diskussion über Unveränderlichkeit. Beachten Sie, dass diese Funktion auf Werten arbeitet, sodass sie Ihnen sagt, dass ein Wert des Typs veränderlich ist, wenn Sie ihr einen `DataType` geben.

!!! Hinweis     Aus technischen Gründen gibt `ismutable` `true` für Werte bestimmter spezieller Typen zurück (zum Beispiel `String` und `Symbol`), obwohl sie nicht auf erlaubte Weise verändert werden können.

Siehe auch [`isbits`](@ref), [`isstructtype`](@ref).

# Beispiele

```jldoctest
julia> ismutable(1)
false

julia> ismutable([1,2])
true
```

!!! kompatibel "Julia 1.5"
    Diese Funktion erfordert mindestens Julia 1.5.


```
