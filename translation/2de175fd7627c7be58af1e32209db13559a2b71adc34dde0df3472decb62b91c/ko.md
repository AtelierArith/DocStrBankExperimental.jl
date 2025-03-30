```
DataType <: Type{T}
```

`DataType`는 이름이 있는 명시적으로 선언된 타입, 명시적으로 선언된 슈퍼타입, 그리고 선택적으로 매개변수를 나타냅니다. 시스템의 모든 구체적인 값은 어떤 `DataType`의 인스턴스입니다.

# 예시

```jldoctest
julia> typeof(Real)
DataType

julia> typeof(Int)
DataType

julia> struct Point
           x::Int
           y
       end

julia> typeof(Point)
DataType
```
