```
@atomiconce a.b.x = value
@atomiconce :sequentially_consistent a.b.x = value
@atomiconce :sequentially_consistent :monotonic a.b.x = value
```

Führen Sie die bedingte Zuweisung von value atomar durch, wenn es zuvor nicht gesetzt war, und geben Sie den Wert `success::Bool` zurück. Dabei zeigt `success` an, ob die Zuweisung abgeschlossen wurde.

Dieser Vorgang entspricht einem Aufruf von `setpropertyonce!(a.b, :x, value)`.

Siehe [Per-field atomics](@ref man-atomics) Abschnitt im Handbuch für weitere Details.

# Beispiele

```jldoctest
julia> mutable struct AtomicOnce
           @atomic x
           AtomicOnce() = new()
       end

julia> a = AtomicOnce()
AtomicOnce(#undef)

julia> @atomiconce a.x = 1 # setze das Feld x von a auf 1, wenn es nicht gesetzt ist, mit sequentieller Konsistenz
true

julia> @atomic a.x # hole das Feld x von a, mit sequentieller Konsistenz
1

julia> @atomiconce a.x = 1 # setze das Feld x von a auf 1, wenn es nicht gesetzt ist, mit sequentieller Konsistenz
false
```

!!! compat "Julia 1.11"
    Diese Funktionalität erfordert mindestens Julia 1.11.

