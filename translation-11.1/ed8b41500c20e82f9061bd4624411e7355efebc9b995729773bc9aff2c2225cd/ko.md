```
front(x::Tuple)::Tuple
```

`x`의 마지막 구성 요소를 제외한 모든 구성 요소로 이루어진 `Tuple`을 반환합니다.

참고: [`first`](@ref), [`tail`](@ref Base.tail).

# 예제

```jldoctest
julia> Base.front((1,2,3))
(1, 2)

julia> Base.front(())
ERROR: ArgumentError: Cannot call front on an empty tuple.
```
