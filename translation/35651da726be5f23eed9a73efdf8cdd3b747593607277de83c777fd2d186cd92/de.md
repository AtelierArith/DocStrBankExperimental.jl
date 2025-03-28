```
isexported(m::Module, s::Symbol) -> Bool
```

Gibt zurück, ob ein Symbol aus einem Modul exportiert wird.

Siehe auch: [`ispublic`](@ref), [`names`](@ref)

```jldoctest
julia> module Mod
           export foo
           public bar
       end
Mod

julia> Base.isexported(Mod, :foo)
true

julia> Base.isexported(Mod, :bar)
false

julia> Base.isexported(Mod, :baz)
false
```
