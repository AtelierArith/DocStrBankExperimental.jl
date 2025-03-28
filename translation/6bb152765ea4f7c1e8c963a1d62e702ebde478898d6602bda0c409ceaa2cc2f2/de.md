```
unsafe_trunc(T, x)
```

Gibt den nächstgelegenen ganzzahligen Wert des Typs `T` zurück, dessen absoluter Wert kleiner oder gleich dem absoluten Wert von `x` ist. Wenn der Wert nicht durch `T` darstellbar ist, wird ein willkürlicher Wert zurückgegeben. Siehe auch [`trunc`](@ref).

# Beispiele

```jldoctest
julia> unsafe_trunc(Int, -2.2)
-2

julia> unsafe_trunc(Int, NaN)
-9223372036854775808
```
