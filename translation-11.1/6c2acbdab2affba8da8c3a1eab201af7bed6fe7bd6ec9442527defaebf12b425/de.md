```
isless(x, y)
```

Testen Sie, ob `x` kleiner als `y` ist, gemäß einer festen Gesamtordnung (definiert zusammen mit [`isequal`](@ref)). `isless` ist nicht für Paare `(x, y)` aller Typen definiert. Wenn es jedoch definiert ist, wird erwartet, dass es die folgenden Bedingungen erfüllt:

  * Wenn `isless(x, y)` definiert ist, dann ist auch `isless(y, x)` und `isequal(x, y)` definiert, und genau eines dieser drei ergibt `true`.
  * Die durch `isless` definierte Relation ist transitiv, d.h. `isless(x, y) && isless(y, z)` impliziert `isless(x, z)`.

Werte, die normalerweise ungeordnet sind, wie `NaN`, werden nach regulären Werten geordnet. [`missing`](@ref) Werte werden zuletzt geordnet.

Dies ist der Standardvergleich, der von [`sort!`](@ref) verwendet wird.

# Implementierung

Nicht-numerische Typen mit einer Gesamtordnung sollten diese Funktion implementieren. Numerische Typen müssen sie nur implementieren, wenn sie spezielle Werte wie `NaN` haben. Typen mit einer partiellen Ordnung sollten [`<`](@ref) implementieren. Siehe die Dokumentation zu [Alternativen Ordnungen](@ref) für Informationen zur Definition alternativer Ordnungsarten, die beim Sortieren und verwandten Funktionen verwendet werden können.

# Beispiele

```jldoctest
julia> isless(1, 3)
true

julia> isless("Red", "Blue")
false
```
