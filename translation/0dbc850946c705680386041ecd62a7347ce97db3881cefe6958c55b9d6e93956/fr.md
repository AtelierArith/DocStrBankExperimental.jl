```
fieldtype(T, name::Symbol | index::Int)
```

Déterminez le type déclaré d'un champ (spécifié par le nom ou l'index) dans un DataType composite `T`.

# Exemples

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
