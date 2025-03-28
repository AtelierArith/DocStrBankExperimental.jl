```
Threads.atomic_xor!(x::Atomic{T}, val::T) where T
```

Atomar bitweise XOR (exklusives Oder) `x` mit `val`

Führt `x[] $= val` atomar aus. Gibt den **alten** Wert zurück.

Für weitere Details siehe LLVMs `atomicrmw xor`-Anweisung.

# Beispiele

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_xor!(x, 7)
5

julia> x[]
2
```
