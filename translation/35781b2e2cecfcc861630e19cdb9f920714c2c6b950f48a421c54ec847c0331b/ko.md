```
only(x)
```

컬렉션 `x`의 유일한 요소를 반환하거나, 컬렉션에 요소가 0개 또는 여러 개 있을 경우 [`ArgumentError`](@ref)를 발생시킵니다.

또한 [`first`](@ref), [`last`](@ref)를 참조하세요.

!!! compat "Julia 1.4"
    이 메서드는 최소한 Julia 1.4가 필요합니다.


# 예제

```jldoctest
julia> only(["a"])
"a"

julia> only("a")
'a': ASCII/Unicode U+0061 (category Ll: Letter, lowercase)

julia> only(())
ERROR: ArgumentError: Tuple contains 0 elements, must contain exactly 1 element
Stacktrace:
[...]

julia> only(('a', 'b'))
ERROR: ArgumentError: Tuple contains 2 elements, must contain exactly 1 element
Stacktrace:
[...]
```
