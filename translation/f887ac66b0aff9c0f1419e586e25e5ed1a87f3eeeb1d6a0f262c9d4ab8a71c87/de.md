```
ispublic(m::Module, s::Symbol) -> Bool
```

Gibt zurück, ob ein Symbol in einem Modul als öffentlich markiert ist.

Exportierte Symbole gelten als öffentlich.

!!! compat "Julia 1.11"
    Diese Funktion und das Konzept der Öffentlichkeitsarbeit wurden in Julia 1.11 hinzugefügt.


Siehe auch: [`isexported`](@ref), [`names`](@ref)

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
