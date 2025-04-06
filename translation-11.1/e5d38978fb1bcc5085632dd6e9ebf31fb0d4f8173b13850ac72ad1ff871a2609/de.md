```
Threads.atomic_cas!(x::Atomic{T}, cmp::T, newval::T) where T
```

Atomar vergleichen und setzen `x`

Vergleicht atomar den Wert in `x` mit `cmp`. Wenn sie gleich sind, wird `newval` in `x` geschrieben. Andernfalls bleibt `x` unverändert. Gibt den alten Wert in `x` zurück. Durch den Vergleich des zurückgegebenen Wertes mit `cmp` (über `===`) weiß man, ob `x` modifiziert wurde und jetzt den neuen Wert `newval` enthält.

Für weitere Details siehe die `cmpxchg`-Anweisung von LLVM.

Diese Funktion kann verwendet werden, um transaktionale Semantiken zu implementieren. Vor der Transaktion wird der Wert in `x` aufgezeichnet. Nach der Transaktion wird der neue Wert nur gespeichert, wenn `x` in der Zwischenzeit nicht modifiziert wurde.

# Beispiele

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_cas!(x, 4, 2);

julia> x
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_cas!(x, 3, 2);

julia> x
Base.Threads.Atomic{Int64}(2)
```
