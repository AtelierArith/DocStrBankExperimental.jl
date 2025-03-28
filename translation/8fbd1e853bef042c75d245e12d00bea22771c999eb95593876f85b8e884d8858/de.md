```
fieldtypes(T::Type)
```

Die deklarierten Typen aller Felder in einem zusammengesetzten Datentyp `T` als ein Tupel.

!!! compat "Julia 1.1"
    Diese Funktion erfordert mindestens Julia 1.1.


# Beispiele

```jldoctest
julia> struct Foo
           x::Int64
           y::String
       end

julia> fieldtypes(Foo)
(Int64, String)
```
