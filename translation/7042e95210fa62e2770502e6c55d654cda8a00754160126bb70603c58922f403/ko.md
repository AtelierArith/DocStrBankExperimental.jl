```
length(collection) -> Integer
```

컬렉션의 요소 수를 반환합니다.

인덱스 가능한 컬렉션의 마지막 유효 인덱스를 얻으려면 [`lastindex`](@ref)를 사용하세요.

참고: [`size`](@ref), [`ndims`](@ref), [`eachindex`](@ref).

# 예제

```jldoctest
julia> length(1:5)
5

julia> length([1, 2, 3, 4])
4

julia> length([1 2; 3 4])
4
```
