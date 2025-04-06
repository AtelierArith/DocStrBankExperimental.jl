```
Base.summarysize(obj; exclude=Union{...}, chargeall=Union{...}) -> Int
```

Berechnet die Menge an Speicher, in Bytes, die von allen einzigartigen Objekten verwendet wird, die vom Argument erreichbar sind.

# Schlüsselwort-Argumente

  * `exclude`: gibt die Typen von Objekten an, die von der Traversierung ausgeschlossen werden sollen.
  * `chargeall`: gibt die Typen von Objekten an, deren Größe aller Felder immer berechnet werden soll, selbst wenn diese Felder normalerweise ausgeschlossen würden.

Siehe auch [`sizeof`](@ref).

# Beispiele

```jldoctest
julia> Base.summarysize(1.0)
8

julia> Base.summarysize(Ref(rand(100)))
848

julia> sizeof(Ref(rand(100)))
8
```
