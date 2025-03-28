```
checkbounds(Bool, A, I...)
```

Gibt `true` zurück, wenn die angegebenen Indizes `I` im Bereich für das gegebene Array `A` liegen. Subtypen von `AbstractArray` sollten diese Methode spezialisieren, wenn sie benutzerdefinierte Überprüfungsverhalten für Grenzen bereitstellen müssen; jedoch kann man in vielen Fällen auf die Indizes von `A` und [`checkindex`](@ref) vertrauen.

Siehe auch [`checkindex`](@ref).

# Beispiele

```jldoctest
julia> A = rand(3, 3);

julia> checkbounds(Bool, A, 2)
true

julia> checkbounds(Bool, A, 3, 4)
false

julia> checkbounds(Bool, A, 1:3)
true

julia> checkbounds(Bool, A, 1:3, 2:4)
false
```
