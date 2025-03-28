```
nameof(t::DataType) -> Symbol
```

Obtiene el nombre de un `DataType` (potencialmente envuelto en `UnionAll`) (sin su módulo padre) como un símbolo.

# Ejemplos

```jldoctest
julia> module Foo
           struct S{T}
           end
       end
Foo

julia> nameof(Foo.S{T} where T)
:S
```
