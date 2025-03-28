```
repeat(A::AbstractArray; inner=ntuple(Returns(1), ndims(A)), outer=ntuple(Returns(1), ndims(A)))
```

Konstruiere ein Array, indem die Einträge von `A` wiederholt werden. Das i-te Element von `inner` gibt an, wie oft die einzelnen Einträge der i-ten Dimension von `A` wiederholt werden sollen. Das i-te Element von `outer` gibt an, wie oft ein Abschnitt entlang der i-ten Dimension von `A` wiederholt werden soll. Wenn `inner` oder `outer` weggelassen werden, erfolgt keine Wiederholung.

# Beispiele

```jldoctest
julia> repeat(1:2, inner=2)
4-element Vector{Int64}:
 1
 1
 2
 2

julia> repeat(1:2, outer=2)
4-element Vector{Int64}:
 1
 2
 1
 2

julia> repeat([1 2; 3 4], inner=(2, 1), outer=(1, 3))
4×6 Matrix{Int64}:
 1  2  1  2  1  2
 1  2  1  2  1  2
 3  4  3  4  3  4
 3  4  3  4  3  4
```
