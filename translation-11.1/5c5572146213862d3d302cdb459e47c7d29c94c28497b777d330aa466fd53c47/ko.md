```
parentmodule(m::Module) -> Module
```

모듈의 포함된 `Module`을 가져옵니다. `Main`은 자신의 부모입니다.

참고: [`names`](@ref), [`nameof`](@ref), [`fullname`](@ref), [`@__MODULE__`](@ref).

# 예제

```jldoctest
julia> parentmodule(Main)
Main

julia> parentmodule(Base.Broadcast)
Base
```
