```
isexported(m::Module, s::Symbol) -> Bool
```

모듈에서 심볼이 내보내졌는지 여부를 반환합니다.

참고: [`ispublic`](@ref), [`names`](@ref)

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
