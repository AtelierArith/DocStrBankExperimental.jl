```
IteratorSize(itertype::Type) -> IteratorSize
```

Gegeben ist der Typ eines Iterators, gibt eine der folgenden Werte zurück:

  * `SizeUnknown()` wenn die Länge (Anzahl der Elemente) im Voraus nicht bestimmt werden kann.
  * `HasLength()` wenn es eine feste, endliche Länge gibt.
  * `HasShape{N}()` wenn eine bekannte Länge plus eine Vorstellung von mehrdimensionaler Form (wie bei einem Array) vorliegt. In diesem Fall sollte `N` die Anzahl der Dimensionen angeben, und die [`axes`](@ref) Funktion ist für den Iterator gültig.
  * `IsInfinite()` wenn der Iterator Werte für immer liefert.

Der Standardwert (für Iteratoren, die diese Funktion nicht definieren) ist `HasLength()`. Das bedeutet, dass die meisten Iteratoren davon ausgehen, die [`length`](@ref) zu implementieren.

Dieses Merkmal wird allgemein verwendet, um zwischen Algorithmen zu wählen, die Platz für ihr Ergebnis vorab reservieren, und Algorithmen, die ihr Ergebnis schrittweise anpassen.

```jldoctest
julia> Base.IteratorSize(1:5)
Base.HasShape{1}()

julia> Base.IteratorSize((2,3))
Base.HasLength()
```
