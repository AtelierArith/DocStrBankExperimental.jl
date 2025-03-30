```
keytype(T::Type{<:AbstractArray})
keytype(A::AbstractArray)
```

배열의 키 유형을 반환합니다. 이는 `keys(...)`의 결과의 [`eltype`](@ref)와 같으며, 주로 사전 인터페이스와의 호환성을 위해 제공됩니다.

# 예제

```jldoctest
julia> keytype([1, 2, 3]) == Int
true

julia> keytype([1 2; 3 4])
CartesianIndex{2}
```

!!! compat "Julia 1.2"
    배열의 경우, 이 함수는 최소한 Julia 1.2가 필요합니다.

