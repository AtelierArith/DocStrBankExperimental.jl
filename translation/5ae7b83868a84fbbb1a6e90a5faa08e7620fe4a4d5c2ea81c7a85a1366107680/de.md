Der Typ `AbstractString` ist der Supertyp aller String-Implementierungen in Julia. Strings sind Kodierungen von Sequenzen von [Unicode](https://unicode.org/) Codepunkten, wie sie durch den Typ `AbstractChar` dargestellt werden. Julia trifft einige Annahmen über Strings:

  * Strings sind in Bezug auf feste "Codeeinheiten" kodiert

      * Codeeinheiten können mit `codeunit(s, i)` extrahiert werden
      * Die erste Codeeinheit hat den Index `1`
      * Die letzte Codeeinheit hat den Index `ncodeunits(s)`
      * Jeder Index `i`, so dass `1 ≤ i ≤ ncodeunits(s)`, ist im Bereich
  * Die String-Indizierung erfolgt in Bezug auf diese Codeeinheiten:

      * Zeichen werden durch `s[i]` mit einem gültigen String-Index `i` extrahiert
      * Jedes `AbstractChar` in einem String wird durch eine oder mehrere Codeeinheiten kodiert
      * Nur der Index der ersten Codeeinheit eines `AbstractChar` ist ein gültiger Index
      * Die Kodierung eines `AbstractChar` ist unabhängig von dem, was ihm vorausgeht oder folgt
      * String-Kodierungen sind [selbstsynchronisierend](https://en.wikipedia.org/wiki/Self-synchronizing_code) – d.h. `isvalid(s, i)` ist O(1)

Einige String-Funktionen, die Codeeinheiten, Zeichen oder Teilstrings aus Strings extrahieren, geben einen Fehler aus, wenn Sie ihnen ungültige oder außerhalb des Bereichs liegende String-Indizes übergeben. Dazu gehören `codeunit(s, i)` und `s[i]`. Funktionen, die String-Indexarithmetik durchführen, gehen entspannter mit der Indizierung um und geben Ihnen den nächstgelegenen gültigen String-Index zurück, wenn er im Bereich liegt, oder verhalten sich, wenn sie außerhalb des Bereichs liegen, so, als ob es eine unendliche Anzahl von Zeichen gibt, die jede Seite des Strings polstern. Normalerweise haben diese imaginären Polsterzeichen eine Codeeinheitslänge von `1`, aber String-Typen können unterschiedliche "imaginäre" Zeichengrößen wählen, die für ihre Implementierungen sinnvoll sind (z.B. können Teilstrings die Indexarithmetik an den zugrunde liegenden String weitergeben, in den sie eine Ansicht bieten). Entspannte Indizierungsfunktionen umfassen diejenigen, die für die Indexarithmetik gedacht sind: `thisind`, `nextind` und `prevind`. Dieses Modell ermöglicht es, dass die Indexarithmetik mit außerhalb des Bereichs liegenden Indizes als Zwischenwerte funktioniert, solange man sie niemals verwendet, um ein Zeichen abzurufen, was oft hilft, die Notwendigkeit zu vermeiden, um Randfälle herum zu codieren.

Siehe auch [`codeunit`](@ref), [`ncodeunits`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref).
