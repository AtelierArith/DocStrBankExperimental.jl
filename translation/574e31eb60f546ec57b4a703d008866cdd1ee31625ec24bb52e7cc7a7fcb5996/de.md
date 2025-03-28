```
cholesky(A::SparseMatrixCSC; shift = 0.0, check = true, perm = nothing) -> CHOLMOD.Factor
```

Berechnen Sie die Cholesky-Zerlegung einer spärlichen positiv definiten Matrix `A`. `A` muss eine [`SparseMatrixCSC`](@ref) oder eine [`Symmetric`](@ref)/[`Hermitian`](@ref) Ansicht einer `SparseMatrixCSC` sein. Beachten Sie, dass `A`, auch wenn es nicht den Typ-Tag hat, dennoch symmetrisch oder hermitisch sein muss. Wenn `perm` nicht angegeben ist, wird eine füllreduzierende Permutation verwendet. `F = cholesky(A)` wird am häufigsten verwendet, um Gleichungssysteme mit `F\b` zu lösen, aber auch die Methoden [`diag`](@ref), [`det`](@ref) und [`logdet`](@ref) sind für `F` definiert. Sie können auch einzelne Faktoren aus `F` extrahieren, indem Sie `F.L` verwenden. Da das Pivotieren standardmäßig aktiviert ist, wird die Zerlegung intern als `A == P'*L*L'*P` mit einer Permutationsmatrix `P` dargestellt; die Verwendung von nur `L` ohne Berücksichtigung von `P` führt zu falschen Ergebnissen. Um die Auswirkungen der Permutation einzubeziehen, ist es typischerweise vorzuziehen, "kombinierte" Faktoren wie `PtL = F.PtL` (das Äquivalent von `P'*L`) und `LtP = F.UP` (das Äquivalent von `L'*P`) zu extrahieren.

Wenn `check = true`, wird ein Fehler ausgelöst, wenn die Zerlegung fehlschlägt. Wenn `check = false`, liegt die Verantwortung für die Überprüfung der Gültigkeit der Zerlegung (über [`issuccess`](@ref)) beim Benutzer.

Durch Setzen des optionalen Schlüsselwortarguments `shift` wird die Zerlegung von `A+shift*I` anstelle von `A` berechnet. Wenn das Argument `perm` angegeben ist, sollte es eine Permutation von `1:size(A,1)` sein, die die zu verwendende Reihenfolge angibt (anstatt der standardmäßigen AMD-Reihenfolge von CHOLMOD).

# Beispiele

Im folgenden Beispiel wird die füllreduzierende Permutation verwendet: `[3, 2, 1]`. Wenn `perm` auf `1:3` gesetzt wird, um keine Permutation zu erzwingen, beträgt die Anzahl der Nicht-Null-Elemente im Faktor 6.

```jldoctest
julia> A = [2 1 1; 1 2 0; 1 0 2]
3×3 Matrix{Int64}:
 2  1  1
 1  2  0
 1  0  2

julia> C = cholesky(sparse(A))
SparseArrays.CHOLMOD.Factor{Float64, Int64}
type:    LLt
method:  simplicial
maxnnz:  5
nnz:     5
success: true

julia> C.p
3-element Vector{Int64}:
 3
 2
 1

julia> L = sparse(C.L);

julia> Matrix(L)
3×3 Matrix{Float64}:
 1.41421   0.0       0.0
 0.0       1.41421   0.0
 0.707107  0.707107  1.0

julia> L * L' ≈ A[C.p, C.p]
true

julia> P = sparse(1:3, C.p, ones(3))
3×3 SparseMatrixCSC{Float64, Int64} mit 3 gespeicherten Einträgen:
  ⋅    ⋅   1.0
  ⋅   1.0   ⋅
 1.0   ⋅    ⋅

julia> P' * L * L' * P ≈ A
true

julia> C = cholesky(sparse(A), perm=1:3)
SparseArrays.CHOLMOD.Factor{Float64, Int64}
type:    LLt
method:  simplicial
maxnnz:  6
nnz:     6
success: true

julia> L = sparse(C.L);

julia> Matrix(L)
3×3 Matrix{Float64}:
 1.41421    0.0       0.0
 0.707107   1.22474   0.0
 0.707107  -0.408248  1.1547

julia> L * L' ≈ A
true
```

!!! note
    Diese Methode verwendet die CHOLMOD[^ACM887][^DavisHager2009] Bibliothek von [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse). CHOLMOD unterstützt nur reale oder komplexe Typen in einfacher oder doppelter Präzision. Eingabematrizen, die nicht diesen Elementtypen entsprechen, werden bei Bedarf in diese Typen konvertiert.

    Viele andere Funktionen von CHOLMOD sind umschlossen, aber nicht aus dem Modul `Base.SparseArrays.CHOLMOD` exportiert.


[^ACM887]: Chen, Y., Davis, T. A., Hager, W. W., & Rajamanickam, S. (2008). Algorithm 887: CHOLMOD, Supernodal Sparse Cholesky Factorization and Update/Downdate. ACM Trans. Math. Softw., 35(3). [doi:10.1145/1391989.1391995](https://doi.org/10.1145/1391989.1391995)

[^DavisHager2009]: Davis, Timothy A., & Hager, W. W. (2009). Dynamic Supernodes in Sparse Cholesky Update/Downdate and Triangular Solves. ACM Trans. Math. Softw., 35(4). [doi:10.1145/1462173.1462176](https://doi.org/10.1145/1462173.1462176)
