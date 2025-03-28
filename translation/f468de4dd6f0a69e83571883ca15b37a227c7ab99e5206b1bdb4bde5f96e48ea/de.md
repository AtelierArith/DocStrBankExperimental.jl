```
Threads.Atomic{T}
```

Hält eine Referenz auf ein Objekt des Typs `T` und stellt sicher, dass es nur atomar, d.h. auf thread-sichere Weise, zugegriffen wird.

Nur bestimmte "einfache" Typen können atomar verwendet werden, nämlich die primitiven booleschen, ganzzahligen und Fließkomma-Typen. Diese sind `Bool`, `Int8`...`Int128`, `UInt8`...`UInt128` und `Float16`...`Float64`.

Neue atomare Objekte können aus nicht-atomaren Werten erstellt werden; wenn nichts angegeben ist, wird das atomare Objekt mit null initialisiert.

Atomare Objekte können mit der `[]`-Notation zugegriffen werden:

# Beispiele

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> x[] = 1
1

julia> x[]
1
```

Atomare Operationen verwenden ein `atomic_`-Präfix, wie z.B. [`atomic_add!`](@ref), [`atomic_xchg!`](@ref) usw.
