```
findnz(A::SparseMatrixCSC)
```

Gibt ein Tupel `(I, J, V)` zurück, wobei `I` und `J` die Zeilen- und Spaltenindizes der gespeicherten ("strukturell nicht null") Werte in der spärlichen Matrix `A` sind, und `V` ein Vektor der Werte ist.

# Beispiele

```jldoctest
julia> A = sparse([1 2 0; 0 0 3; 0 4 0])
3×3 SparseMatrixCSC{Int64, Int64} mit 4 gespeicherten Einträgen:
 1  2  ⋅
 ⋅  ⋅  3
 ⋅  4  ⋅

julia> findnz(A)
([1, 1, 3, 2], [1, 2, 2, 3], [1, 2, 4, 3])
```
