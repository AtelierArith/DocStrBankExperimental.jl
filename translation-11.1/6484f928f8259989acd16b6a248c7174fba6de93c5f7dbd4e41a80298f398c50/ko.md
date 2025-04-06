```
sizeof(T::DataType)
sizeof(obj)
```

주어진 `DataType` `T`의 표준 이진 표현의 크기(바이트 단위)입니다. 또는 `DataType`이 아닌 경우 객체 `obj`의 크기(바이트 단위)입니다.

자세한 내용은 [`Base.summarysize`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> sizeof(Float32)
4

julia> sizeof(ComplexF64)
16

julia> sizeof(1.0)
8

julia> sizeof(collect(1.0:10.0))
80

julia> struct StructWithPadding
           x::Int64
           flag::Bool
       end

julia> sizeof(StructWithPadding) # 패딩으로 인해 필드의 `sizeof` 합계가 아님
16

julia> sizeof(Int64) + sizeof(Bool) # 위와 다름
9
```

`DataType` `T`에 특정 크기가 없는 경우 오류가 발생합니다.

```jldoctest
julia> sizeof(AbstractArray)
ERROR: Abstract type AbstractArray does not have a definite size.
Stacktrace:
[...]
```
