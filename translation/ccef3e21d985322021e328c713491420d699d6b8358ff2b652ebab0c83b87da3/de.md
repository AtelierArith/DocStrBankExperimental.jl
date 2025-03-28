```
Threads.atomic_min!(x::Atomic{T}, val::T) where T
```

Speichert atomar das Minimum von `x` und `val` in `x`

Führt `x[] = min(x[], val)` atomar aus. Gibt den **alten** Wert zurück.

Für weitere Details siehe LLVMs `atomicrmw min`-Anweisung.

# Beispiele

```jldoctest
julia> x = Threads.Atomic{Int}(7)
Base.Threads.Atomic{Int64}(7)

julia> Threads.atomic_min!(x, 5)
7

julia> x[]
5
```
