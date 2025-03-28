```
last(coll)
```

Holen Sie sich das letzte Element einer geordneten Sammlung, wenn es in O(1) Zeit berechnet werden kann. Dies wird erreicht, indem [`lastindex`](@ref) aufgerufen wird, um den letzten Index zu erhalten. Gibt den Endpunkt eines [`AbstractRange`](@ref) zurück, auch wenn er leer ist.

Siehe auch [`first`](@ref), [`endswith`](@ref).

# Beispiele

```jldoctest
julia> last(1:2:10)
9

julia> last([1; 2; 3; 4])
4
```
