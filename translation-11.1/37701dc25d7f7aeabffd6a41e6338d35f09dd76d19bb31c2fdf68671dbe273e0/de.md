```
Threads.atomic_nand!(x::Atomic{T}, val::T) where T
```

Atomar bitweise nand (nicht-und) `x` mit `val`

Führt `x[] = ~(x[] & val)` atomar aus. Gibt den **alten** Wert zurück.

Für weitere Details siehe LLVMs `atomicrmw nand` Anweisung.

# Beispiele

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_nand!(x, 2)
3

julia> x[]
-3
```
