```
ispublic(m::Module, s::Symbol) -> Bool
```

Bir sembolün bir modülde kamuya açık olarak işaretlenip işaretlenmediğini döndürür.

Dışa aktarılan semboller kamuya açık olarak kabul edilir.

!!! compat "Julia 1.11"
    Bu işlev ve kamuya açıklık kavramı Julia 1.11'de eklendi.


Ayrıca bakınız: [`isexported`](@ref), [`names`](@ref)

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
