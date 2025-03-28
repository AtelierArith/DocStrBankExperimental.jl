```
Threads.atomic_sub!(x::Atomic{T}, val::T) where T <: ArithmeticTypes
```

Zieht `val` atomar von `x` ab.

Führt `x[] -= val` atomar aus. Gibt den **alten** Wert zurück. Nicht definiert für `Atomic{Bool}`.

Für weitere Details siehe LLVMs `atomicrmw sub`-Anweisung.

# Beispiele

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_sub!(x, 2)
3

julia> x[]
1
```
