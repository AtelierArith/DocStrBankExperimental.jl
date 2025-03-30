```
product(iters...)
```

여러 반복자의 곱에 대한 반복기를 반환합니다. 생성된 각 요소는 `i`번째 요소가 `i`번째 인수 반복자에서 오는 튜플입니다. 첫 번째 반복자가 가장 빠르게 변경됩니다.

참고: [`zip`](@ref), [`Iterators.flatten`](@ref).

# 예제

```jldoctest
julia> collect(Iterators.product(1:2, 3:5))
2×3 Matrix{Tuple{Int64, Int64}}:
 (1, 3)  (1, 4)  (1, 5)
 (2, 3)  (2, 4)  (2, 5)

julia> ans == [(x,y) for x in 1:2, y in 3:5]  # Iterators.product을 포함하는 생성기를 수집합니다.
true
```
