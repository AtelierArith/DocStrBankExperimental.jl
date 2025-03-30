```
takewhile(pred, iter)
```

`iter`에서 `pred`가 참인 동안 요소를 생성하는 반복자이며, 그 이후에는 모든 요소를 버립니다.

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

julia> collect(Iterators.takewhile(<(3),s))
2-element Vector{Int64}:
 1
 2
```
