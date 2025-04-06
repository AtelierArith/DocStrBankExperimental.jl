```
Core.Type{T}
```

`Core.Type`는 모든 타입 객체를 인스턴스로 가지는 추상 타입입니다. 단일톤 타입 `Core.Type{T}`의 유일한 인스턴스는 객체 `T`입니다.

# 예제

```jldoctest
julia> isa(Type{Float64}, Type)
true

julia> isa(Float64, Type)
true

julia> isa(Real, Type{Float64})
false

julia> isa(Real, Type{Real})
true
```
