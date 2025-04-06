```
vec(a::AbstractArray) -> AbstractVector
```

배열 `a`를 1차원 열 벡터로 변환합니다. `a`가 이미 `AbstractVector`인 경우 `a`를 반환합니다. 결과 배열은 `a`와 동일한 기본 데이터를 공유하므로, `a`가 변경 가능할 경우에만 변경 가능하며, 이 경우 하나를 수정하면 다른 것도 수정됩니다.

# 예제

```jldoctest
julia> a = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> vec(a)
6-element Vector{Int64}:
 1
 4
 2
 5
 3
 6

julia> vec(1:3)
1:3
```

또한 [`reshape`](@ref), [`dropdims`](@ref)를 참조하세요.
