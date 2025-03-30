```
nameof(m::Module) -> Symbol
```

`Module`의 이름을 [`Symbol`](@ref)로 가져옵니다.

# 예제

```jldoctest
julia> nameof(Base.Broadcast)
:Broadcast
```
