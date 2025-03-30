```
findnext(predicate::Function, A, i)
```

`predicate`가 `true`를 반환하는 `A`의 요소의 다음 인덱스를 `i` 이후 또는 포함하여 찾습니다. 찾지 못한 경우 `nothing`을 반환합니다. 이는 [`getindex`](@ref), [`keys(A)`](@ref), 및 [`nextind`](@ref)를 지원하는 배열, 문자열 및 대부분의 다른 컬렉션에서 작동합니다.

인덱스는 [`keys(A)`](@ref) 및 [`pairs(A)`](@ref)에서 반환된 것과 동일한 유형입니다.

# 예제

```jldoctest
julia> A = [1, 4, 2, 2];

julia> findnext(isodd, A, 1)
1

julia> findnext(isodd, A, 2) # nothing을 반환하지만 REPL에 출력되지 않음

julia> A = [1 4; 2 2];

julia> findnext(isodd, A, CartesianIndex(1, 1))
CartesianIndex(1, 1)

julia> findnext(isspace, "a b c", 3)
4
```
