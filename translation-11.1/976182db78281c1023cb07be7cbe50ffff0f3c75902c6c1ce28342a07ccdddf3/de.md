```
nzrange(A::AbstractSparseMatrixCSC, col::Integer)
```

Gibt den Bereich der Indizes zu den strukturellen Nicht-Null-Werten einer Spalten eines spärlichen Matrizen zurück. In Verbindung mit [`nonzeros`](@ref) und [`rowvals`](@ref) ermöglicht dies ein bequemes Iterieren über eine spärliche Matrix:

```
A = sparse(I,J,V)
rows = rowvals(A)
vals = nonzeros(A)
m, n = size(A)
for j = 1:n
   for i in nzrange(A, j)
      row = rows[i]
      val = vals[i]
      # führe spärliche Zauberei aus...
   end
end
```

!!! warning
    Das Hinzufügen oder Entfernen von Nicht-Null-Elementen zur Matrix kann die `nzrange` ungültig machen, man sollte die Matrix während des Iterierens nicht verändern.

