```
fieldtypes(T::Type)
```

Les types déclarés de tous les champs dans un DataType composite `T` sous forme de tuple.

!!! compat "Julia 1.1"
    Cette fonction nécessite au moins Julia 1.1.


# Exemples

```jldoctest
julia> struct Foo
           x::Int64
           y::String
       end

julia> fieldtypes(Foo)
(Int64, String)
```
