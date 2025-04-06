```
UndefRefError()
```

Das Element oder Feld ist für das gegebene Objekt nicht definiert.

# Beispiele

```jldoctest
julia> struct MyType
           a::Vector{Int}
           MyType() = new()
       end

julia> A = MyType()
MyType(#undef)

julia> A.a
ERROR: UndefRefError: Zugriff auf undefinierten Verweis
Stacktrace:
[...]
```
