```
fieldtypes(T::Type)
```

복합 데이터 타입 `T`의 모든 필드에 대한 선언된 타입을 튜플로 반환합니다.

!!! compat "Julia 1.1"
    이 함수는 최소한 Julia 1.1이 필요합니다.


# 예제

```jldoctest
julia> struct Foo
           x::Int64
           y::String
       end

julia> fieldtypes(Foo)
(Int64, String)
```
