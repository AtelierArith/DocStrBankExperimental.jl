```
subtypes(T::DataType)
```

DataType `T`의 즉각적인 하위 유형 목록을 반환합니다. 현재 로드된 모든 하위 유형이 포함되며, 현재 모듈에서 보이지 않는 하위 유형도 포함됩니다.

또한 [`supertype`](@ref), [`supertypes`](@ref), [`methodswith`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> subtypes(Integer)
3-element Vector{Any}:
 Bool
 Signed
 Unsigned
```
