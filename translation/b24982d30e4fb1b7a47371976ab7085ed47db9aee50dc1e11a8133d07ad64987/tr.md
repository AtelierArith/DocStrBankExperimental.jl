```
nameof(t::DataType) -> Symbol
```

Bir (potansiyel olarak `UnionAll` ile sarılmış) `DataType`'in adını (ebeveyn modülü olmadan) bir sembol olarak alır.

# Örnekler

```jldoctest
julia> module Foo
           struct S{T}
           end
       end
Foo

julia> nameof(Foo.S{T} where T)
:S
```
