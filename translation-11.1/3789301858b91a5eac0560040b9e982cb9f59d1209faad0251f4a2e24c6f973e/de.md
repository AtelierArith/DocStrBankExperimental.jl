```
skipmissing(itr)
```

Gibt einen Iterator über die Elemente in `itr` zurück, der [`missing`](@ref) Werte überspringt. Das zurückgegebene Objekt kann mit Indizes von `itr` indiziert werden, wenn letzterer indizierbar ist. Indizes, die entsprechenden fehlenden Werten zugeordnet sind, sind nicht gültig: Sie werden von [`keys`](@ref) und [`eachindex`](@ref) übersprungen, und eine `MissingException` wird ausgelöst, wenn versucht wird, sie zu verwenden.

Verwenden Sie [`collect`](@ref), um ein `Array` zu erhalten, das die nicht-`missing` Werte in `itr` enthält. Beachten Sie, dass das Ergebnis immer ein `Vector` sein wird, selbst wenn `itr` ein mehrdimensionales Array ist, da es nicht möglich ist, fehlende Werte zu entfernen und gleichzeitig die Dimensionen des Eingangs zu erhalten.

Siehe auch [`coalesce`](@ref), [`ismissing`](@ref), [`something`](@ref).

# Beispiele

```jldoctest
julia> x = skipmissing([1, missing, 2])
skipmissing(Union{Missing, Int64}[1, missing, 2])

julia> sum(x)
3

julia> x[1]
1

julia> x[2]
ERROR: MissingException: der Wert an Index (2,) ist fehlend
[...]

julia> argmax(x)
3

julia> collect(keys(x))
2-element Vector{Int64}:
 1
 3

julia> collect(skipmissing([1, missing, 2]))
2-element Vector{Int64}:
 1
 2

julia> collect(skipmissing([1 missing; 2 missing]))
2-element Vector{Int64}:
 1
 2
```
