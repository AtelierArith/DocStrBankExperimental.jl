```
tail(x::Tuple)::Tuple
```

`x`의 첫 번째 구성 요소를 제외한 모든 요소로 구성된 `Tuple`을 반환합니다.

참고: [`front`](@ref Base.front), [`rest`](@ref Base.rest), [`first`](@ref), [`Iterators.peel`](@ref).

# 예제

```jldoctest
julia> Base.tail((1,2,3))
(2, 3)

julia> Base.tail(())
ERROR: ArgumentError: Cannot call tail on an empty tuple.
```
