```
@atomicswap a.b.x = neu
@atomicswap :sequentially_consistent a.b.x = neu
```

Speichert `neu` in `a.b.x` und gibt den alten Wert von `a.b.x` zurück.

Diese Operation übersetzt sich in einen `swapproperty!(a.b, :x, neu)` Aufruf.

Siehe [Per-field atomics](@ref man-atomics) Abschnitt im Handbuch für weitere Details.

# Beispiele

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomicswap a.x = 2+2 # ersetze Feld x von a mit 4, mit sequentieller Konsistenz
1

julia> @atomic a.x # hole Feld x von a, mit sequentieller Konsistenz
4
```

!!! compat "Julia 1.7"
    Diese Funktionalität erfordert mindestens Julia 1.7.

