```
@atomicreplace a.b.x erwartet => gewünscht
@atomicreplace :sequentially_consistent a.b.x erwartet => gewünscht
@atomicreplace :sequentially_consistent :monotonic a.b.x erwartet => gewünscht
```

Führen Sie den bedingten Austausch, der durch das Paar ausgedrückt wird, atomar durch und geben Sie die Werte `(alt, erfolg::Bool)` zurück. Dabei zeigt `erfolg`, ob der Austausch abgeschlossen wurde.

Dieser Vorgang entspricht einem `replaceproperty!(a.b, :x, erwartet, gewünscht)` Aufruf.

Siehe [Per-field atomics](@ref man-atomics) Abschnitt im Handbuch für weitere Details.

# Beispiele

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomicreplace a.x 1 => 2 # ersetze Feld x von a mit 2, wenn es 1 war, mit sequentieller Konsistenz
(alt = 1, erfolg = true)

julia> @atomic a.x # hole Feld x von a, mit sequentieller Konsistenz
2

julia> @atomicreplace a.x 1 => 2 # ersetze Feld x von a mit 2, wenn es 1 war, mit sequentieller Konsistenz
(alt = 2, erfolg = false)

julia> xchg = 2 => 0; # ersetze Feld x von a mit 0, wenn es 2 war, mit sequentieller Konsistenz

julia> @atomicreplace a.x xchg
(alt = 2, erfolg = true)

julia> @atomic a.x # hole Feld x von a, mit sequentieller Konsistenz
0
```

!!! kompatibel "Julia 1.7"
    Diese Funktionalität erfordert mindestens Julia 1.7.

