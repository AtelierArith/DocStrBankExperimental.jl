```
ispublic(m::Module, s::Symbol) -> Bool
```

Renvoie si un symbole est marqué comme public dans un module.

Les symboles exportés sont considérés comme publics.

!!! compat "Julia 1.11"
    Cette fonction et la notion de publicité ont été ajoutées dans Julia 1.11.


Voir aussi : [`isexported`](@ref), [`names`](@ref)

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
