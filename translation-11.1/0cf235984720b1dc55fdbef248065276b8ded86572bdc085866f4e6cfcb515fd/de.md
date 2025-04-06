```
ldlt(A::SparseMatrixCSC; shift = 0.0, check = true, perm=nothing) -> CHOLMOD.Factor
```

Berechnen Sie die $LDL'$-Faktorisierung einer spärlichen Matrix `A`. `A` muss eine [`SparseMatrixCSC`](@ref) oder eine [`Symmetric`](@ref)/[`Hermitian`](@ref) Ansicht einer `SparseMatrixCSC` sein. Beachten Sie, dass `A`, auch wenn es nicht den Typ-Tag hat, dennoch symmetrisch oder hermitesch sein muss. Eine füllreduzierende Permutation wird verwendet. `F = ldlt(A)` wird am häufigsten verwendet, um Gleichungssysteme `A*x = b` mit `F\b` zu lösen. Das zurückgegebene Faktorisierungsobjekt `F` unterstützt auch die Methoden [`diag`](@ref), [`det`](@ref), [`logdet`](@ref) und [`inv`](@ref). Sie können einzelne Faktoren aus `F` mit `F.L` extrahieren. Da jedoch das Pivoting standardmäßig aktiviert ist, wird die Faktorisierung intern als `A == P'*L*D*L'*P` mit einer Permutationsmatrix `P` dargestellt; die Verwendung von nur `L` ohne Berücksichtigung von `P` führt zu falschen Ergebnissen. Um die Auswirkungen der Permutation einzubeziehen, ist es typischerweise vorzuziehen, "kombinierte" Faktoren wie `PtL = F.PtL` (das Äquivalent von `P'*L`) und `LtP = F.UP` (das Äquivalent von `L'*P`) zu extrahieren. Die vollständige Liste der unterstützten Faktoren ist `:L, :PtL, :D, :UP, :U, :LD, :DU, :PtLD, :DUP`.

Wenn `check = true`, wird ein Fehler ausgelöst, wenn die Zerlegung fehlschlägt. Wenn `check = false`, liegt die Verantwortung für die Überprüfung der Gültigkeit der Zerlegung (über [`issuccess`](@ref)) beim Benutzer.

Durch Setzen des optionalen Schlüsselwortarguments `shift` wird die Faktorisierung von `A+shift*I` anstelle von `A` berechnet. Wenn das Argument `perm` bereitgestellt wird, sollte es eine Permutation von `1:size(A,1)` sein, die die zu verwendende Reihenfolge angibt (anstatt der standardmäßigen AMD-Reihenfolge von CHOLMOD).

!!! Hinweis     Diese Methode verwendet die CHOLMOD[^ACM887][^DavisHager2009] Bibliothek von [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse). CHOLMOD unterstützt nur reale oder komplexe Typen in einfacher oder doppelter Präzision. Eingabematrizen, die nicht diesen Elementtypen entsprechen, werden bei Bedarf in diese Typen konvertiert.

```
Viele andere Funktionen von CHOLMOD sind verpackt, aber nicht aus dem Modul `Base.SparseArrays.CHOLMOD` exportiert.
```
