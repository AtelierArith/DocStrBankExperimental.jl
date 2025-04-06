```
end
```

`end`는 표현식 블록의 결론을 나타내며, 예를 들어 [`module`](@ref), [`struct`](@ref), [`mutable struct`](@ref), [`begin`](@ref), [`let`](@ref), [`for`](@ref) 등이 있습니다.

`end`는 또한 인덱싱할 때 컬렉션의 마지막 인덱스 또는 배열의 차원의 마지막 인덱스를 나타내는 데 사용될 수 있습니다.

# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Array{Int64, 2}:
 1  2
 3  4

julia> A[end, :]
2-element Array{Int64, 1}:
 3
 4
```
