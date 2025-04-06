```
IteratorEltype(itertype::Type) -> IteratorEltype
```

Gegeben ist der Typ eines Iterators, gibt einen der folgenden Werte zurück:

  * `EltypeUnknown()` wenn der Typ der von dem Iterator erzeugten Elemente im Voraus nicht bekannt ist.
  * `HasEltype()` wenn der Elementtyp bekannt ist und [`eltype`](@ref) einen sinnvollen Wert zurückgeben würde.

`HasEltype()` ist der Standard, da davon ausgegangen wird, dass Iteratoren [`eltype`](@ref) implementieren.

Dieses Merkmal wird allgemein verwendet, um zwischen Algorithmen zu wählen, die einen bestimmten Typ von Ergebnis vorab zuweisen, und Algorithmen, die einen Ergebnistyp basierend auf den Typen der erzeugten Werte auswählen.

```jldoctest
julia> Base.IteratorEltype(1:5)
Base.HasEltype()
```
