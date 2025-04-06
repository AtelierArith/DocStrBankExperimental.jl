```
Threads.atomic_max!(x::Atomic{T}, val::T) where T
```

Speichert atomar das Maximum von `x` und `val` in `x`

Führt `x[] = max(x[], val)` atomar aus. Gibt den **alten** Wert zurück.

Für weitere Details siehe LLVMs `atomicrmw max`-Anweisung.

# Beispiele

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_max!(x, 7)
5

julia> x[]
7
```
