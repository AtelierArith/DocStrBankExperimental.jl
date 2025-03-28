```
fieldtype(T, name::Symbol | index::Int)
```

Bestimmen Sie den deklarierten Typ eines Feldes (angegeben durch Namen oder Index) in einem zusammengesetzten Datentyp `T`.

# Beispiele

```jldoctest
julia> struct Foo
           x::Int64
           y::String
       end

julia> fieldtype(Foo, :x)
Int64

julia> fieldtype(Foo, 2)
String
```
