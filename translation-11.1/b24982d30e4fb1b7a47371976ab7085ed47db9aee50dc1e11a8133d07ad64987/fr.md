```
nameof(t::DataType) -> Symbol
```

Obtenez le nom d'un `DataType` (potentiellement enveloppé dans `UnionAll`) (sans son module parent) sous forme de symbole.

# Exemples

```jldoctest
julia> module Foo
           struct S{T}
           end
       end
Foo

julia> nameof(Foo.S{T} where T)
:S
```
