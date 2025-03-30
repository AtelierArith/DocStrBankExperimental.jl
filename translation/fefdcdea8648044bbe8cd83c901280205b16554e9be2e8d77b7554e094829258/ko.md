```
Iterators.map(f, iterators...)
```

지연 매핑을 생성합니다. 이는 `(f(args...) for args in zip(iterators...))`를 작성하는 또 다른 구문입니다.

!!! compat "Julia 1.6"
    이 함수는 최소한 Julia 1.6이 필요합니다.


# 예제

```jldoctest
julia> collect(Iterators.map(x -> x^2, 1:3))
3-element Vector{Int64}:
 1
 4
 9
```
