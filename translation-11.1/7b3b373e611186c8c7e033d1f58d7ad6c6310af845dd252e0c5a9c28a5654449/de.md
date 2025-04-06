```
halfperm!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{TvA,Ti},
          q::AbstractVector{<:Integer}, f::Function = identity) where {Tv,TvA,Ti}
```

Spaltenumordnung und Transponierung von `A`, während gleichzeitig `f` auf jeden Eintrag von `A` angewendet wird, wobei das Ergebnis `(f(A)Q)^T` (`map(f, transpose(A[:,q]))`) in `X` gespeichert wird.

Der Elementtyp `Tv` von `X` muss mit `f(::TvA)` übereinstimmen, wobei `TvA` der Elementtyp von `A` ist. Die Dimensionen von `X` müssen mit denen von `transpose(A)` übereinstimmen (`size(X, 1) == size(A, 2)` und `size(X, 2) == size(A, 1)`), und `X` muss über genügend Speicherplatz verfügen, um alle zugewiesenen Einträge in `A` aufzunehmen (`length(rowvals(X)) >= nnz(A)` und `length(nonzeros(X)) >= nnz(A)`). Die Länge der Spaltenpermutation `q` muss mit der Spaltenanzahl von `A` übereinstimmen (`length(q) == size(A, 2)`).

Diese Methode ist die Elternmethode mehrerer Methoden, die Transpositions- und Permutationsoperationen auf [`SparseMatrixCSC`](@ref)s durchführen. Da diese Methode keine Argumentüberprüfung durchführt, sollten die sichereren Kindmethoden (`[c]transpose[!]`, `permute[!]`) der direkten Verwendung vorgezogen werden.

Diese Methode implementiert den `HALFPERM`-Algorithmus, der in F. Gustavson, "Two fast algorithms for sparse matrices: multiplication and permuted transposition," ACM TOMS 4(3), 250-269 (1978) beschrieben ist. Der Algorithmus läuft in `O(size(A, 1), size(A, 2), nnz(A))` Zeit und benötigt keinen zusätzlichen Speicher über das hinaus, was übergeben wird.
