```
valtype(T::Type{<:AbstractArray})
valtype(A::AbstractArray)
```

배열의 값 유형을 반환합니다. 이는 [`eltype`](@ref)와 동일하며 주로 사전 인터페이스와의 호환성을 위해 제공됩니다.

# 예제

```jldoctest
julia> valtype(["one", "two", "three"])
String
```

!!! compat "Julia 1.2"
    배열의 경우, 이 함수는 최소한 Julia 1.2가 필요합니다.

