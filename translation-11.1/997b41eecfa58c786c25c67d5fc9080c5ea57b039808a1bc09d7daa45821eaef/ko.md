```
setdiff(s, itrs...)
```

`s`에 있는 요소 중 `itrs`의 어떤 반복 가능한 객체에도 없는 요소의 집합을 구성합니다. 배열의 순서를 유지합니다.

자세한 내용은 [`setdiff!`](@ref), [`union`](@ref) 및 [`intersect`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> setdiff([1,2,3], [3,4,5])
2-element Vector{Int64}:
 1
 2
```
