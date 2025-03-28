```
parentmodule(t::DataType) -> Module
```

Determina el módulo que contiene la definición de un `DataType` (potencialmente envuelto en `UnionAll`).

# Ejemplos

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
