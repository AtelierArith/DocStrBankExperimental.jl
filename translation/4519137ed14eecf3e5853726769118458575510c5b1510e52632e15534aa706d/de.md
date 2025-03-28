```
isequal(x, y) -> Bool
```

Ähnlich wie [`==`](@ref), mit Ausnahme der Behandlung von Fließkommazahlen und fehlenden Werten. `isequal` behandelt alle Fließkomma-`NaN`-Werte als gleich zueinander, behandelt `-0.0` als ungleich `0.0` und [`missing`](@ref) als gleich zu `missing`. Gibt immer einen `Bool`-Wert zurück.

`isequal` ist eine Äquivalenzrelation - sie ist reflexiv (`===` impliziert `isequal`), symmetrisch (`isequal(a, b)` impliziert `isequal(b, a)`) und transitiv (`isequal(a, b)` und `isequal(b, c)` impliziert `isequal(a, c)`).

# Implementierung

Die Standardimplementierung von `isequal` ruft `==` auf, sodass ein Typ, der keine Fließkommawerte enthält, im Allgemeinen nur `==` definieren muss.

`isequal` ist die Vergleichsfunktion, die von Hash-Tabellen (`Dict`) verwendet wird. `isequal(x,y)` muss implizieren, dass `hash(x) == hash(y)`.

Das bedeutet typischerweise, dass Typen, für die eine benutzerdefinierte `==`- oder `isequal`-Methode existiert, eine entsprechende [`hash`](@ref)-Methode implementieren müssen (und umgekehrt). Sammlungen implementieren typischerweise `isequal`, indem sie `isequal` rekursiv auf allen Inhalten aufrufen.

Darüber hinaus ist `isequal` mit [`isless`](@ref) verknüpft, und sie arbeiten zusammen, um eine feste totale Ordnung zu definieren, bei der genau einer von `isequal(x, y)`, `isless(x, y)` oder `isless(y, x)` `true` sein muss (und die anderen beiden `false`).

Skalare Typen müssen im Allgemeinen `isequal` nicht separat von `==` implementieren, es sei denn, sie repräsentieren Fließkommazahlen, die eine effizientere Implementierung als die bereitgestellte generische Rückfallimplementierung (basierend auf `isnan`, `signbit` und `==`) ermöglichen.

# Beispiele

```jldoctest
julia> isequal([1., NaN], [1., NaN])
true

julia> [1., NaN] == [1., NaN]
false

julia> 0.0 == -0.0
true

julia> isequal(0.0, -0.0)
false

julia> missing == missing
missing

julia> isequal(missing, missing)
true
```
