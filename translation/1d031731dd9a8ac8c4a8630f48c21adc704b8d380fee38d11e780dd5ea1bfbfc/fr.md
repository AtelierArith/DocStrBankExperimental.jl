```
UndefRefError()
```

L'élément ou le champ n'est pas défini pour l'objet donné.

# Exemples

```jldoctest
julia> struct MyType
           a::Vector{Int}
           MyType() = new()
       end

julia> A = MyType()
MyType(#undef)

julia> A.a
ERROR: UndefRefError: accès à une référence indéfinie
Stacktrace:
[...]
```
