```
union(s, itrs...)
∪(s, itrs...)
```

Konstruiere ein Objekt, das alle unterschiedlichen Elemente aus allen Argumenten enthält.

Das erste Argument steuert, welche Art von Container zurückgegeben wird. Wenn dies ein Array ist, wird die Reihenfolge beibehalten, in der die Elemente zuerst erscheinen.

Unicode `∪` kann eingegeben werden, indem `\cup` geschrieben und dann die Tabulatortaste im Julia REPL und in vielen Editoren gedrückt wird. Dies ist ein infix Operator, der `s ∪ itr` ermöglicht.

Siehe auch [`unique`](@ref), [`intersect`](@ref), [`isdisjoint`](@ref), [`vcat`](@ref), [`Iterators.flatten`](@ref).

# Beispiele

```jldoctest
julia> union([1, 2], [3])
3-element Vector{Int64}:
 1
 2
 3

julia> union([4 2 3 4 4], 1:3, 3.0)
4-element Vector{Float64}:
 4.0
 2.0
 3.0
 1.0

julia> (0, 0.0) ∪ (-0.0, NaN)
3-element Vector{Real}:
   0
  -0.0
 NaN

julia> union(Set([1, 2]), 2:3)
Set{Int64} with 3 elements:
  2
  3
  1
```
