```
setfield!(value, name::Symbol, x, [order::Symbol])
setfield!(value, i::Int, x, [order::Symbol])
```

Weisen Sie `x` einem benannten Feld in `value` eines zusammengesetzten Typs zu. Der `value` muss veränderlich sein und `x` muss ein Untertyp von `fieldtype(typeof(value), name)` sein. Zusätzlich kann eine Reihenfolge für diese Operation angegeben werden. Wenn das Feld als `@atomic` deklariert wurde, ist diese Spezifikation obligatorisch. Andernfalls, wenn es nicht als `@atomic` deklariert wurde, muss es `:not_atomic` sein, wenn es angegeben wird. Siehe auch [`setproperty!`](@ref Base.setproperty!).

# Beispiele

```jldoctest
julia> mutable struct MyMutableStruct
           field::Int
       end

julia> a = MyMutableStruct(1);

julia> setfield!(a, :field, 2);

julia> getfield(a, :field)
2

julia> a = 1//2
1//2

julia> setfield!(a, :num, 3);
ERROR: setfield!: immutable struct of type Rational cannot be changed
```
