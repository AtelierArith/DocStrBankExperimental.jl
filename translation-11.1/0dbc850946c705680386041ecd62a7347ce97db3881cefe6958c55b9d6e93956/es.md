```
fieldtype(T, name::Symbol | index::Int)
```

Determina el tipo declarado de un campo (especificado por nombre o índice) en un tipo de dato compuesto `T`.

# Ejemplos

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
