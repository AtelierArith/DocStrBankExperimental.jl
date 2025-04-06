```
length(A::AbstractArray)
```

배열의 요소 수를 반환하며, 기본값은 `prod(size(A))`입니다.

# 예제

```jldoctest
julia> length([1, 2, 3, 4])
4

julia> length([1 2; 3 4])
4
```
