```
dropwhile(pred, iter)
```

`iter`에서 `pred`가 참인 동안 요소를 제거하고, 그 이후에는 모든 요소를 반환하는 반복자입니다.

!!! compat "Julia 1.4"
    이 함수는 최소한 Julia 1.4가 필요합니다.


# 예제

```jldoctest
julia> s = collect(1:5)
5-element Vector{Int64}:
 1
 2
 3
 4
 5

julia> collect(Iterators.dropwhile(<(3),s))
3-element Vector{Int64}:
 3
 4
 5
```
