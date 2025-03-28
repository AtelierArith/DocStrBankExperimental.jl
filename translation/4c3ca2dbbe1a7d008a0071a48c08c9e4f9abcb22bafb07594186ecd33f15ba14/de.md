```
parentmodule(t::DataType) -> Modul
```

Bestimmen Sie das Modul, das die Definition eines (möglicherweise `UnionAll`-umhüllten) `DataType` enthält.

# Beispiele

```jldoctest
julia> module Foo
           struct Int end
       end
Foo

julia> parentmodule(Int)
Core

julia> parentmodule(Foo.Int)
Foo
```
