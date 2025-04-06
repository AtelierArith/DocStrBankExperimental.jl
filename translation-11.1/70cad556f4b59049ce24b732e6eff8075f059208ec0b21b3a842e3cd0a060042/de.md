```
getfield(value, name::Symbol, [order::Symbol])
getfield(value, i::Int, [order::Symbol])
```

Extrahiert ein Feld aus einem zusammengesetzten `value` nach Name oder Position. Optional kann eine Reihenfolge für die Operation definiert werden. Wenn das Feld als `@atomic` deklariert wurde, wird empfohlen, dass die Spezifikation mit den Speicherungen an diesem Ort kompatibel ist. Andernfalls, wenn es nicht als `@atomic` deklariert ist, muss dieser Parameter, falls angegeben, `:not_atomic` sein. Siehe auch [`getproperty`](@ref Base.getproperty) und [`fieldnames`](@ref).

# Beispiele

```jldoctest
julia> a = 1//2
1//2

julia> getfield(a, :num)
1

julia> a.num
1

julia> getfield(a, 1)
1
```
