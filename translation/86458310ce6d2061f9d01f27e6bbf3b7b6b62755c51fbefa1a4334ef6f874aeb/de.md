```
==(x, y)
```

Generischer Gleichheitsoperator. Fällt zurück auf [`===`](@ref). Sollte für alle Typen mit einem Konzept von Gleichheit implementiert werden, basierend auf dem abstrakten Wert, den eine Instanz repräsentiert. Zum Beispiel werden alle numerischen Typen nach ihrem numerischen Wert verglichen, unabhängig vom Typ. Strings werden als Zeichenfolgen verglichen, wobei die Kodierung ignoriert wird. Sammlungen desselben Typs vergleichen im Allgemeinen ihre Schlüsselsätze, und wenn diese `==` sind, vergleichen sie die Werte für jeden dieser Schlüssel und geben true zurück, wenn alle solchen Paare `==` sind. Andere Eigenschaften werden typischerweise nicht berücksichtigt (wie der genaue Typ).

Dieser Operator folgt den IEEE-Semantiken für Fließkommazahlen: `0.0 == -0.0` und `NaN != NaN`.

Das Ergebnis ist vom Typ `Bool`, es sei denn, einer der Operanden ist [`missing`](@ref), in diesem Fall wird `missing` zurückgegeben ([dreiwertige Logik](https://de.wikipedia.org/wiki/Dreiwertige_Logik)). Sammlungen implementieren im Allgemeinen eine dreiwertige Logik ähnlich wie [`all`](@ref), wobei missing zurückgegeben wird, wenn einer der Operanden fehlende Werte enthält und alle anderen Paare gleich sind. Verwenden Sie [`isequal`](@ref) oder [`===`](@ref), um immer ein `Bool`-Ergebnis zu erhalten.

# Implementierung

Neue numerische Typen sollten diese Funktion für zwei Argumente des neuen Typs implementieren und den Vergleich mit anderen Typen, wo möglich, über Promotionsregeln handhaben.

[`isequal`](@ref) fällt auf `==` zurück, sodass neue Methoden von `==` vom [`Dict`](@ref)-Typ verwendet werden, um Schlüssel zu vergleichen. Wenn Ihr Typ als Schlüssel in einem Wörterbuch verwendet wird, sollte er daher auch [`hash`](@ref) implementieren.

Wenn ein Typ `==`, [`isequal`](@ref) und [`isless`](@ref) definiert, sollte er auch [`<`](@ref) implementieren, um die Konsistenz der Vergleiche sicherzustellen.
