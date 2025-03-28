```
lu(A::AbstractSparseMatrixCSC; check = true, q = nothing, control = get_umfpack_control()) -> F::UmfpackLU
```

Berechnen Sie die LU-Zerlegung einer spärlichen Matrix `A`.

Für spärliche `A` mit reellem oder komplexem Elementtyp ist der Rückgabewert von `F` `UmfpackLU{Tv, Ti}`, wobei `Tv` = [`Float64`](@ref) oder `ComplexF64` entsprechend und `Ti` ein ganzzahliger Typ ([`Int32`](@ref) oder [`Int64`](@ref)) ist.

Wenn `check = true`, wird ein Fehler ausgelöst, wenn die Zerlegung fehlschlägt. Wenn `check = false`, liegt die Verantwortung für die Überprüfung der Gültigkeit der Zerlegung (über [`issuccess`](@ref)) beim Benutzer.

Der Permutationsvektor `q` kann entweder ein Permutationsvektor oder `nothing` sein. Wenn kein Permutationsvektor bereitgestellt wird oder `q` `nothing` ist, wird das Standardverhalten von UMFPACK verwendet. Wenn die Permutation nicht nullbasiert ist, wird eine nullbasierte Kopie erstellt.

Der `control`-Vektor hat standardmäßig die Standardkonfiguration des Julia SparseArrays-Pakets für UMFPACK (NB: dies wurde von den UMFPACK-Standardeinstellungen geändert, um die iterative Verfeinerung zu deaktivieren), kann jedoch geändert werden, indem ein Vektor der Länge `UMFPACK_CONTROL` übergeben wird. Siehe das UMFPACK-Handbuch für mögliche Konfigurationen. Um beispielsweise die iterative Verfeinerung wieder zu aktivieren:

```
umfpack_control = SparseArrays.UMFPACK.get_umfpack_control(Float64, Int64) # Julia-Standardkonfiguration für eine Float64-spärliche Matrix lesen
SparseArrays.UMFPACK.show_umf_ctrl(umfpack_control) # optional - Werte anzeigen
umfpack_control[SparseArrays.UMFPACK.JL_UMFPACK_IRSTEP] = 2.0 # iterative Verfeinerung wieder aktivieren (2 ist UMFPACK-Standard für maximale Schritte der iterativen Verfeinerung)

Alu = lu(A; control = umfpack_control)
x = Alu \ b   # löse Ax = b, einschließlich der iterativen Verfeinerung von UMFPACK
```

Die einzelnen Komponenten der Zerlegung `F` können durch Indizierung zugegriffen werden:

| Komponente | Beschreibung                              |
|:---------- |:----------------------------------------- |
| `L`        | `L` (untere Dreiecksmatrix) Teil von `LU` |
| `U`        | `U` (obere Dreiecksmatrix) Teil von `LU`  |
| `p`        | rechte Permutation `Vector`               |
| `q`        | linke Permutation `Vector`                |
| `Rs`       | `Vector` der Skalierungsfaktoren          |
| `:`        | `(L,U,p,q,Rs)` Komponenten                |

Die Beziehung zwischen `F` und `A` ist

`F.L*F.U == (F.Rs .* A)[F.p, F.q]`

`F` unterstützt außerdem die folgenden Funktionen:

  * [`\`](@ref)
  * [`det`](@ref)

Siehe auch [`lu!`](@ref)

!!! Hinweis     `lu(A::AbstractSparseMatrixCSC)` verwendet die UMFPACK[^ACM832] Bibliothek, die Teil von [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse) ist. Da diese Bibliothek nur spärliche Matrizen mit [`Float64`](@ref) oder `ComplexF64`-Elementen unterstützt, konvertiert `lu` `A` in eine Kopie, die vom Typ `SparseMatrixCSC{Float64}` oder `SparseMatrixCSC{ComplexF64}` ist, je nach Bedarf.

[^ACM832]: Davis, Timothy A. (2004b). Algorithm 832: UMFPACK V4.3–-eine unsymmetrische Muster-Multifrontal-Methode. ACM Trans. Math. Softw., 30(2), 196–199. [doi:10.1145/992200.992206](https://doi.org/10.1145/992200.992206)
