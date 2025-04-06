```
intersect(s, itrs...)
∩(s, itrs...)
```

Konstruiere die Menge, die diejenigen Elemente enthält, die in allen Argumenten erscheinen.

Das erste Argument steuert, welche Art von Container zurückgegeben wird. Wenn dies ein Array ist, wird die Reihenfolge beibehalten, in der die Elemente zuerst erscheinen.

Unicode `∩` kann eingegeben werden, indem `\cap` geschrieben und dann die Tabulatortaste im Julia REPL und in vielen Editoren gedrückt wird. Dies ist ein infix Operator, der `s ∩ itr` ermöglicht.

Siehe auch [`setdiff`](@ref), [`isdisjoint`](@ref), [`issubset`](@ref Base.issubset), [`issetequal`](@ref).

!!! compat "Julia 1.8"
    Ab Julia 1.8 gibt intersect ein Ergebnis mit dem eltype der typ-promoteten eltypes der beiden Eingaben zurück.


# Beispiele

```jldoctest
julia> intersect([1, 2, 3], [3, 4, 5])
1-element Vector{Int64}:
 3

julia> intersect([1, 4, 4, 5, 6], [6, 4, 6, 7, 8])
2-element Vector{Int64}:
 4
 6

julia> intersect(1:16, 7:99)
7:16

julia> (0, 0.0) ∩ (-0.0, 0)
1-element Vector{Real}:
 0

julia> intersect(Set([1, 2]), BitSet([2, 3]), 1.0:10.0)
Set{Float64} mit 1 Element:
  2.0
```
