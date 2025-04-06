```
fieldtypes(T::Type)
```

Los tipos declarados de todos los campos en un DataType compuesto `T` como una tupla.

!!! compat "Julia 1.1"
    Esta función requiere al menos Julia 1.1.


# Ejemplos

```jldoctest
julia> struct Foo
           x::Int64
           y::String
       end

julia> fieldtypes(Foo)
(Int64, String)
```
