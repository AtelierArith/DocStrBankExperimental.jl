```
+(x, y...)
```

Addition Operator.

Infix `x+y+z+...` ruft diese Funktion mit allen Argumenten auf, d.h. `+(x, y, z, ...)`, die standardmäßig dann `(x+y) + z + ...` von links nach rechts aufruft.

Beachten Sie, dass Überlauf für die meisten Ganzzahltypen, einschließlich des Standardtyps `Int`, möglich ist, wenn große Zahlen addiert werden.

# Beispiele

```jldoctest
julia> 1 + 20 + 4
25

julia> +(1, 20, 4)
25

julia> [1,2] + [3,4]
2-element Vector{Int64}:
 4
 6

julia> typemax(Int) + 1 < 0
true
```
