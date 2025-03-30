```
minimum(itr; [init])
```

컬렉션에서 가장 작은 요소를 반환합니다.

빈 `itr`에 대해 반환되는 값은 `init`으로 지정할 수 있습니다. `init`은 `min`에 대한 중립 요소여야 하며(즉, 다른 모든 요소보다 크거나 같아야 함) 빈 컬렉션이 아닌 경우 `init`이 사용되는지는 명시되어 있지 않습니다.

!!! compat "Julia 1.6"
    키워드 인수 `init`은 Julia 1.6 이상이 필요합니다.


# 예제

```jldoctest
julia> minimum(-20.5:10)
-20.5

julia> minimum([1,2,3])
1

julia> minimum([])
ERROR: ArgumentError: reducing over an empty collection is not allowed; consider supplying `init` to the reducer
Stacktrace:
[...]

julia> minimum([]; init=Inf)
Inf
```
