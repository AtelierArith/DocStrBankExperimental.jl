```
isdefined(m::Module, s::Symbol, [order::Symbol])
isdefined(object, s::Symbol, [order::Symbol])
isdefined(object, index::Int, [order::Symbol])
```

Überprüft, ob eine globale Variable oder ein Objektfeld definiert ist. Die Argumente können ein Modul und ein Symbol oder ein zusammengesetztes Objekt und der Feldname (als Symbol) oder Index sein. Optional kann eine Reihenfolge für die Operation definiert werden. Wenn das Feld als `@atomic` deklariert wurde, wird empfohlen, dass die Spezifikation mit den Speicheroperationen an diesem Ort kompatibel ist. Andernfalls, wenn es nicht als `@atomic` deklariert ist, muss dieser Parameter, falls angegeben, `:not_atomic` sein.

Um zu testen, ob ein Array-Element definiert ist, verwenden Sie [`isassigned`](@ref) stattdessen.

Siehe auch [`@isdefined`](@ref).

# Beispiele

```jldoctest
julia> isdefined(Base, :sum)
true

julia> isdefined(Base, :NonExistentMethod)
false

julia> a = 1//2;

julia> isdefined(a, 2)
true

julia> isdefined(a, 3)
false

julia> isdefined(a, :num)
true

julia> isdefined(a, :numerator)
false
```
