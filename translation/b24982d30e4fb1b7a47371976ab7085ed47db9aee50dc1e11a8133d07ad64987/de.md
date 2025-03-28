```
nameof(t::DataType) -> Symbol
```

Holen Sie sich den Namen eines (möglicherweise `UnionAll`-umhüllten) `DataType` (ohne sein übergeordnetes Modul) als Symbol.

# Beispiele

```jldoctest
julia> module Foo
           struct S{T}
           end
       end
Foo

julia> nameof(Foo.S{T} where T)
:S
```
