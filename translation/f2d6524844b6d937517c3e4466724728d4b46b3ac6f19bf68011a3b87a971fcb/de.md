```
Threads.atomic_or!(x::Atomic{T}, val::T) where T
```

Atomar bitweise oder `x` mit `val`

Führt `x[] |= val` atomar aus. Gibt den **alten** Wert zurück.

Für weitere Details siehe LLVMs `atomicrmw or` Anweisung.

# Beispiele

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_or!(x, 7)
5

julia> x[]
7
```
