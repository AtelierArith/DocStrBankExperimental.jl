```
sparse!(I::AbstractVector{Ti}, J::AbstractVector{Ti}, V::AbstractVector{Tv},
        m::Integer, n::Integer, combine, klasttouch::Vector{Ti},
        csrrowptr::Vector{Ti}, csrcolval::Vector{Ti}, csrnzval::Vector{Tv},
        [csccolptr::Vector{Ti}], [cscrowval::Vector{Ti}, cscnzval::Vector{Tv}] ) where {Tv,Ti<:Integer}
```

Elternteil und Expertenfahrer für [`sparse`](@ref); siehe [`sparse`](@ref) für die grundlegende Verwendung. Diese Methode ermöglicht es dem Benutzer, vorab zugewiesenen Speicher für die Zwischenobjekte und das Ergebnis von `sparse` bereitzustellen, wie unten beschrieben. Diese Fähigkeit ermöglicht eine effizientere aufeinanderfolgende Konstruktion von [`SparseMatrixCSC`](@ref)s aus Koordinatenrepräsentationen und ermöglicht auch die Extraktion einer unsortierten Spaltenrepräsentation der Transponierten des Ergebnisses ohne zusätzliche Kosten.

Diese Methode besteht aus drei Hauptschritten: (1) Zähl-Sortierung der bereitgestellten Koordinatenrepräsentation in eine unsortierte Zeilen-CSR-Form einschließlich wiederholter Einträge. (2) Durchfegen der CSR-Form, während gleichzeitig das gewünschte Spaltenzeiger-Array der CSC-Form berechnet, wiederholte Einträge erkannt und die CSR-Form mit kombinierten wiederholten Einträgen neu verpackt wird; diese Phase ergibt eine unsortierte Zeilen-CSR-Form ohne wiederholte Einträge. (3) Zähl-Sortierung der vorhergehenden CSR-Form in eine vollständig sortierte CSC-Form ohne wiederholte Einträge.

Die Eingabearrays `csrrowptr`, `csrcolval` und `csrnzval` stellen den Speicher für die Zwischen-CSR-Formen dar und erfordern `length(csrrowptr) >= m + 1`, `length(csrcolval) >= length(I)` und `length(csrnzval >= length(I))`. Das Eingabearray `klasttouch`, der Arbeitsbereich für die zweite Phase, erfordert `length(klasttouch) >= n`. Optionale Eingabearrays `csccolptr`, `cscrowval` und `cscnzval` stellen den Speicher für die zurückgegebene CSC-Form `S` dar. Falls erforderlich, werden diese automatisch so angepasst, dass `length(csccolptr) = n + 1`, `length(cscrowval) = nnz(S)` und `length(cscnzval) = nnz(S)`; daher genügt es, leere Vektoren des entsprechenden Typs (`Vector{Ti}()` und `Vector{Tv}()`) zu übergeben, oder die Methode `sparse!` aufzurufen, ohne `cscrowval` und `cscnzval` zu berücksichtigen.

Bei der Rückgabe enthalten `csrrowptr`, `csrcolval` und `csrnzval` eine unsortierte Spaltenrepräsentation der Transponierten des Ergebnisses.

Sie können den Speicher der Eingabearrays (`I`, `J`, `V`) für die Ausgabearrays (`csccolptr`, `cscrowval`, `cscnzval`) wiederverwenden. Zum Beispiel können Sie `sparse!(I, J, V, csrrowptr, csrcolval, csrnzval, I, J, V)` aufrufen. Beachten Sie, dass sie angepasst werden, um die oben genannten Bedingungen zu erfüllen.

Im Interesse der Effizienz führt diese Methode keine Argumentüberprüfung über `1 <= I[k] <= m` und `1 <= J[k] <= n` hinaus durch. Verwenden Sie sie mit Vorsicht. Es ist ratsam, mit `--check-bounds=yes` zu testen.

Diese Methode läuft in `O(m, n, length(I))` Zeit. Der HALFPERM-Algorithmus, der in F. Gustavson, "Two fast algorithms for sparse matrices: multiplication and permuted transposition," ACM TOMS 4(3), 250-269 (1978) beschrieben wird, inspirierte die Verwendung eines Paares von Zähl-Sortierungen in dieser Methode.
