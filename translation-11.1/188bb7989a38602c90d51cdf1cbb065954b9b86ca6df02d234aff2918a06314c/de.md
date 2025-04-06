```
@timev expr
@timev "beschreibung" expr
```

Dies ist eine ausführliche Version des `@time` Makros. Es druckt zuerst die gleichen Informationen wie `@time`, dann alle nicht-null Speicherzuweisungszähler und gibt dann den Wert des Ausdrucks zurück.

Optional kann eine Beschreibung als Zeichenfolge angegeben werden, die vor dem Zeitbericht ausgegeben wird.

!!! compat "Julia 1.8"
    Die Option, eine Beschreibung hinzuzufügen, wurde in Julia 1.8 eingeführt.


Siehe auch [`@time`](@ref), [`@timed`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref) und [`@allocations`](@ref).

```julia-repl
julia> x = rand(10,10);

julia> @timev x * x;
  0.546770 Sekunden (2.20 M Zuweisungen: 116.632 MiB, 4.23% gc Zeit, 99.94% Kompilierungszeit)
verstrichene Zeit (ns): 546769547
gc Zeit (ns):          23115606
zugewiesene Bytes:     122297811
Pool-Zuweisungen:      2197930
nicht-Pool GC-Zuweisungen: 1327
malloc() Aufrufe:      36
realloc() Aufrufe:     5
GC Pausen:            3

julia> @timev x * x;
  0.000010 Sekunden (1 Zuweisung: 896 Bytes)
verstrichene Zeit (ns): 9848
zugewiesene Bytes:     896
Pool-Zuweisungen:      1
```
