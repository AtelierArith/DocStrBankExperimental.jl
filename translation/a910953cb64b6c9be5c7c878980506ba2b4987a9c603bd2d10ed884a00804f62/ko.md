```
rest(iter, state)
```

주어진 `state`에서 시작하여 `iter`와 동일한 요소를 생성하는 반복자입니다.

참고: [`Iterators.drop`](@ref), [`Iterators.peel`](@ref), [`Base.rest`](@ref).

# 예제

```jldoctest
julia> collect(Iterators.rest([1,2,3,4], 2))
3-element Vector{Int64}:
 2
 3
 4
```
