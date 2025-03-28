```
UndefRefError()
```

El ítem o campo no está definido para el objeto dado.

# Ejemplos

```jldoctest
julia> struct MyType
           a::Vector{Int}
           MyType() = new()
       end

julia> A = MyType()
MyType(#undef)

julia> A.a
ERROR: UndefRefError: acceso a referencia indefinida
Stacktrace:
[...]
```
