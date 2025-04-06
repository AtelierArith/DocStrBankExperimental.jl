```
ispublic(m::Module, s::Symbol) -> Bool
```

Devuelve si un símbolo está marcado como público en un módulo.

Los símbolos exportados se consideran públicos.

!!! compat "Julia 1.11"
    Esta función y la noción de publicidad se añadieron en Julia 1.11.


Véase también: [`isexported`](@ref), [`names`](@ref)

```jldoctest
julia> module Mod
           export foo
           public bar
       end
Mod

julia> Base.ispublic(Mod, :foo)
true

julia> Base.ispublic(Mod, :bar)
true

julia> Base.ispublic(Mod, :baz)
false
```
