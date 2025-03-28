```
lu(A, pivot = RowMaximum(); check = true, allowsingular = false) -> F::LU
```

Berechnen Sie die LU-Zerlegung von `A`.

Wenn `check = true` ist, wird ein Fehler ausgelöst, wenn die Zerlegung fehlschlägt. Wenn `check = false` ist, liegt die Verantwortung für die Überprüfung der Gültigkeit der Zerlegung (über [`issuccess`](@ref)) beim Benutzer.

Standardmäßig wird mit `check = true` auch ein Fehler ausgelöst, wenn die Zerlegung gültige Faktoren produziert, aber der obere dreieckige Faktor `U` rangdefizient ist. Dies kann geändert werden, indem `allowsingular = true` übergeben wird.

In den meisten Fällen, wenn `A` ein Subtyp `S` von `AbstractMatrix{T}` mit einem Elementtyp `T` ist, der `+`, `-`, `*` und `/` unterstützt, ist der Rückgabetyp `LU{T,S{T}}`.

Im Allgemeinen umfasst die LU-Zerlegung eine Permutation der Zeilen der Matrix (entsprechend der `F.p` Ausgabe, die unten beschrieben ist), bekannt als "Pivotierung" (weil sie entspricht, welche Zeile den "Pivot" enthält, den diagonalen Eintrag von `F.U`). Eine der folgenden Pivotierungsstrategien kann über das optionale Argument `pivot` ausgewählt werden:

  * `RowMaximum()` (Standard): die Standard-Pivotierungsstrategie; der Pivot entspricht dem Element mit dem maximalen Absolutwert unter den verbleibenden, zu zerlegenden Zeilen. Diese Pivotierungsstrategie erfordert, dass der Elementtyp auch [`abs`](@ref) und [`<`](@ref) unterstützt. (Dies ist im Allgemeinen die einzige numerisch stabile Option für Gleitkommatrizen.)
  * `RowNonZero()`: der Pivot entspricht dem ersten nicht-null Element unter den verbleibenden, zu zerlegenden Zeilen. (Dies entspricht der typischen Wahl in Handberechnungen und ist auch nützlich für allgemeinere algebraische Zahlentypen, die [`iszero`](@ref) unterstützen, aber nicht `abs` oder `<`.)
  * `NoPivot()`: Pivotierung deaktiviert (schlägt fehl, wenn ein Null-Eintrag in einer Pivot-Position auftritt, selbst wenn `allowsingular = true`).

Die einzelnen Komponenten der Zerlegung `F` können über [`getproperty`](@ref) abgerufen werden:

| Komponente | Beschreibung                          |
|:---------- |:------------------------------------- |
| `F.L`      | `L` (untere dreieckige) Teil von `LU` |
| `F.U`      | `U` (obere dreieckige) Teil von `LU`  |
| `F.p`      | (rechte) Permutation `Vector`         |
| `F.P`      | (rechte) Permutation `Matrix`         |

Die Iteration über die Zerlegung produziert die Komponenten `F.L`, `F.U` und `F.p`.

Die Beziehung zwischen `F` und `A` ist

`F.L*F.U == A[F.p, :]`

`F` unterstützt außerdem die folgenden Funktionen:

| Unterstützte Funktion | `LU` | `LU{T,Tridiagonal{T}}` |
|:--------------------- |:---- |:---------------------- |
| [`/`](@ref)           | ✓    |                        |
| [`\`](@ref)           | ✓    | ✓                      |
| [`inv`](@ref)         | ✓    | ✓                      |
| [`det`](@ref)         | ✓    | ✓                      |
| [`logdet`](@ref)      | ✓    | ✓                      |
| [`logabsdet`](@ref)   | ✓    | ✓                      |
| [`size`](@ref)        | ✓    | ✓                      |

!!! compat "Julia 1.11"
    Das Schlüsselwortargument `allowsingular` wurde in Julia 1.11 hinzugefügt.


# Beispiele

```jldoctest
julia> A = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> F = lu(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L-Faktor:
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
U-Faktor:
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> F.L * F.U == A[F.p, :]
true

julia> l, u, p = lu(A); # Destrukturierung über Iteration

julia> l == F.L && u == F.U && p == F.p
true

julia> lu([1 2; 1 2], allowsingular = true)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L-Faktor:
2×2 Matrix{Float64}:
 1.0  0.0
 1.0  1.0
U-Faktor (rangdefizient):
2×2 Matrix{Float64}:
 1.0  2.0
 0.0  0.0
```
