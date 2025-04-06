```
symdiff(s, itrs...)
```

전달된 집합의 요소들 간의 대칭 차집합을 구성합니다. `s`가 `AbstractSet`이 아닐 경우, 순서가 유지됩니다.

또한 [`symdiff!`](@ref), [`setdiff`](@ref), [`union`](@ref) 및 [`intersect`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> symdiff([1,2,3], [3,4,5], [4,5,6])
3-element Vector{Int64}:
 1
 2
 6

julia> symdiff([1,2,1], [2, 1, 2])
Int64[]
```
