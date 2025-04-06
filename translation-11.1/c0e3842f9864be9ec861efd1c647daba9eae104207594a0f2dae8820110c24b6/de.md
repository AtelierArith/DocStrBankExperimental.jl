```
permute!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti},
         p::AbstractVector{<:Integer}, q::AbstractVector{<:Integer},
         [C::AbstractSparseMatrixCSC{Tv,Ti}]) where {Tv,Ti}
```

Bilateral permutation von `A`, Speicherung des Ergebnisses `PAQ` (`A[p,q]`) in `X`. Speichert das Zwischenergebnis `(AQ)^T` (`transpose(A[:,q])`) im optionalen Argument `C`, falls vorhanden. Es wird vorausgesetzt, dass `X`, `A` und, falls vorhanden, `C` sich nicht gegenseitig aliasieren; um das Ergebnis `PAQ` zurück in `A` zu speichern, verwenden Sie die folgende Methode ohne `X`:

```
permute!(A::AbstractSparseMatrixCSC{Tv,Ti}, p::AbstractVector{<:Integer},
         q::AbstractVector{<:Integer}[, C::AbstractSparseMatrixCSC{Tv,Ti},
         [workcolptr::Vector{Ti}]]) where {Tv,Ti}
```

Die Dimensionen von `X` müssen mit denen von `A` übereinstimmen (`size(X, 1) == size(A, 1)` und `size(X, 2) == size(A, 2)`), und `X` muss über genügend Speicherplatz verfügen, um alle zugewiesenen Einträge in `A` aufzunehmen (`length(rowvals(X)) >= nnz(A)` und `length(nonzeros(X)) >= nnz(A)`). Die Länge der Spaltenpermutation `q` muss mit der Spaltenanzahl von `A` übereinstimmen (`length(q) == size(A, 2)`). Die Länge der Zeilenpermutation `p` muss mit der Zeilenanzahl von `A` übereinstimmen (`length(p) == size(A, 1)`).

Die Dimensionen von `C` müssen mit denen von `transpose(A)` übereinstimmen (`size(C, 1) == size(A, 2)` und `size(C, 2) == size(A, 1)`), und `C` muss über genügend Speicherplatz verfügen, um alle zugewiesenen Einträge in `A` aufzunehmen (`length(rowvals(C)) >= nnz(A)` und `length(nonzeros(C)) >= nnz(A)`).

Für zusätzliche (algorithmische) Informationen und für Versionen dieser Methoden, die auf die Argumentüberprüfung verzichten, siehe (nicht exportierte) Elternmethoden `unchecked_noalias_permute!` und `unchecked_aliasing_permute!`.

Siehe auch [`permute`](@ref).
