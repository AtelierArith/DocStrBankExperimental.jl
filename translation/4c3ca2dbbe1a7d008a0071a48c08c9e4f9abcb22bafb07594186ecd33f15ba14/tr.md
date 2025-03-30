```
parentmodule(t::DataType) -> Modül
```

Bir (potansiyel olarak `UnionAll` ile sarılmış) `DataType` tanımını içeren modülü belirleyin.

# Örnekler

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
