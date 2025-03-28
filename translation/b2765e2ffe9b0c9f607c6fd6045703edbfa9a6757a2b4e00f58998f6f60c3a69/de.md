```
Threads.atomic_xchg!(x::Atomic{T}, newval::T) where T
```

Atomar den Wert in `x` austauschen

Austausch des Wertes in `x` mit `newval` auf atomare Weise. Gibt den **alten** Wert zurück.

Für weitere Details siehe die `atomicrmw xchg`-Anweisung von LLVM.

# Beispiele

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_xchg!(x, 2)
3

julia> x[]
2
```
