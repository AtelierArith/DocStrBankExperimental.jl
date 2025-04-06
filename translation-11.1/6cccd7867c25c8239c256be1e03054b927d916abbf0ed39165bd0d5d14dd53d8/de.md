```
spzeros([type], I::AbstractVector, J::AbstractVector, [m, n])
```

Erstellen Sie eine spärliche Matrix `S` mit den Dimensionen `m x n` mit strukturellen Nullen bei `S[I[k], J[k]]`.

Diese Methode kann verwendet werden, um das Sparsamkeitsmuster der Matrix zu konstruieren und ist effizienter als z.B. `sparse(I, J, zeros(length(I)))`.

Für zusätzliche Dokumentation und einen Experten-Treiber siehe `SparseArrays.spzeros!`.

!!! compat "Julia 1.10"
    Diese Methode erfordert Julia-Version 1.10 oder höher.

