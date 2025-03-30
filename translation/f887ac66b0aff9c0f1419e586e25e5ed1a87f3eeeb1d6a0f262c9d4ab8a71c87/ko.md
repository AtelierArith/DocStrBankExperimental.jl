```
ispublic(m::Module, s::Symbol) -> Bool
```

모듈에서 기호가 공개로 표시되었는지 여부를 반환합니다.

내보낸 기호는 공개로 간주됩니다.

!!! compat "Julia 1.11"
    이 함수와 공개성 개념은 Julia 1.11에 추가되었습니다.


참고: [`isexported`](@ref), [`names`](@ref)

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
