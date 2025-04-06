```
parentmodule(t::DataType) -> Module
```

Déterminez le module contenant la définition d'un `DataType` (potentiellement enveloppé dans `UnionAll`).

# Exemples

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
