```
x::EscapeInfo
```

Ein Gitter für Fluchtinformationen, das die folgenden Eigenschaften enthält:

  * `x.Analyzed::Bool`: nicht formell Teil des Gitters, zeigt nur an, ob `x` analysiert wurde
  * `x.ReturnEscape::Bool`: zeigt an, dass `x` über die Rückgabe zum Aufrufer entkommen kann
  * `x.ThrownEscape::BitSet`: zeichnet SSA-Anweisungsnummern auf, an denen `x` als Ausnahme geworfen werden kann:

      * `isempty(x.ThrownEscape)`: `x` wird in diesem Aufrufrahmen niemals geworfen (das Minimum)
      * `pc ∈ x.ThrownEscape`: `x` kann an der SSA-Anweisung bei `pc` geworfen werden
      * `-1 ∈ x.ThrownEscape`: `x` kann an beliebigen Punkten dieses Aufrufrahmens geworfen werden (das Maximum)

    Diese Informationen werden von `escape_exception!` verwendet, um potenzielle Fluchten über Ausnahmen zu propagieren.
  * `x.AliasInfo::Union{Bool,IndexableFields,IndexableElements,Unindexable}`: verwaltet alle möglichen Werte, die auf Felder oder Array-Elemente von `x` aliasiert werden können:

      * `x.AliasInfo === false` zeigt an, dass die Felder/Elemente von `x` noch nicht analysiert wurden
      * `x.AliasInfo === true` zeigt an, dass die Felder/Elemente von `x` nicht analysiert werden können, z. B. ist der Typ von `x` nicht bekannt oder nicht konkret, und daher können seine Felder/Elemente nicht genau bekannt sein
      * `x.AliasInfo::IndexableFields` zeichnet alle möglichen Werte auf, die auf Felder des Objekts `x` mit präzisen Indexinformationen aliasiert werden können
      * `x.AliasInfo::IndexableElements` zeichnet alle möglichen Werte auf, die auf Elemente des Arrays `x` mit präzisen Indexinformationen aliasiert werden können
      * `x.AliasInfo::Unindexable` zeichnet alle möglichen Werte auf, die auf Felder/Elemente von `x` ohne präzise Indexinformationen aliasiert werden können
  * `x.Liveness::BitSet`: zeichnet SSA-Anweisungsnummern auf, an denen `x` lebendig sein sollte, z. B. um als Aufrufargument verwendet zu werden, um an einen Aufrufer zurückgegeben zu werden oder für `:foreigncall` erhalten zu bleiben:

      * `isempty(x.Liveness)`: `x` wird in diesem Aufrufrahmen niemals verwendet (das Minimum)
      * `0 ∈ x.Liveness` hat auch die besondere Bedeutung, dass es ein Aufrufargument des derzeit analysierten Aufrufrahmens ist (und somit sofort vom Aufrufer sichtbar ist).
      * `pc ∈ x.Liveness`: `x` kann an der SSA-Anweisung bei `pc` verwendet werden
      * `-1 ∈ x.Liveness`: `x` kann an beliebigen Punkten dieses Aufrufrahmens verwendet werden (das Maximum)

Es gibt Hilfskonstruktoren, um gängige `EscapeInfo`s zu erstellen, z. B.:

  * `NoEscape()`: das Minimum(-ähnliche) Element dieses Gitters, was bedeutet, dass es nirgendwohin entkommen wird
  * `AllEscape()`: das oberste Element dieses Gitters, was bedeutet, dass es überallhin entkommen wird

`analyze_escapes` wird diese Elemente vom Minimum zum Maximum überführen, in die gleiche Richtung wie Julias native Typinferenzroutine. Ein abstrakter Zustand wird mit den Minimum(-ähnlichen) Elementen initialisiert:

  * die Aufrufargumente werden als `ArgEscape()` initialisiert, dessen `Liveness`-Eigenschaft `0` enthält, um anzuzeigen, dass es als Aufrufargument übergeben wird und sofort vom Aufrufer sichtbar ist
  * die anderen Zustände werden als `NotAnalyzed()` initialisiert, was ein spezielles Gitterelement ist, das etwas niedriger als `NoEscape` ist, aber gleichzeitig keine andere Bedeutung hat, als dass es noch nicht analysiert wurde (und somit nicht formell Teil des Gitters ist)
