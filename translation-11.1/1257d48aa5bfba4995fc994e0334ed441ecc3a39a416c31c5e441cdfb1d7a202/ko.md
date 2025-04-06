```
unique!(f, A::AbstractVector)
```

`A`의 요소에 적용된 `f`에 의해 생성된 각 고유 값에 대해 `A`에서 하나의 값을 선택한 다음 수정된 `A`를 반환합니다.

!!! compat "Julia 1.1"
    이 메서드는 Julia 1.1부터 사용할 수 있습니다.


# 예제

```jldoctest
julia> unique!(x -> x^2, [1, -1, 3, -3, 4])
3-element Vector{Int64}:
 1
 3
 4

julia> unique!(n -> n%3, [5, 1, 8, 9, 3, 4, 10, 7, 2, 6])
3-element Vector{Int64}:
 5
 1
 9

julia> unique!(iseven, [2, 3, 5, 7, 9])
2-element Vector{Int64}:
 2
 3
```
