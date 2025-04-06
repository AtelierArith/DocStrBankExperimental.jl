```
empty(v::AbstractVector, [eltype])
```

`v`와 유사한 빈 벡터를 생성하며, 선택적으로 `eltype`을 변경할 수 있습니다.

참고: [`empty!`](@ref), [`isempty`](@ref), [`isassigned`](@ref).

# 예제

```jldoctest
julia> empty([1.0, 2.0, 3.0])
Float64[]

julia> empty([1.0, 2.0, 3.0], String)
String[]
```
