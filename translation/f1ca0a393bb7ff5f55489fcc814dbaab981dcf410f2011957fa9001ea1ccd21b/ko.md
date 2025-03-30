```
extrema(itr; [init]) -> (mn, mx)
```

단일 패스에서 최소값 `mn`과 최대값 `mx` 요소를 모두 계산하고, 이를 2-튜플로 반환합니다.

빈 `itr`에 대해 반환되는 값은 `init`으로 지정할 수 있습니다. 이는 `min` 및 `max`에 대한 중립 요소인 첫 번째 및 두 번째 요소를 가진 2-튜플이어야 합니다(즉, 다른 모든 요소보다 크거나 작거나 같아야 함). 결과적으로, `itr`이 비어 있을 때 반환된 `(mn, mx)` 튜플은 `mn ≥ mx`를 만족합니다. `init`이 지정되면 비어 있지 않은 `itr`에 대해서도 사용할 수 있습니다.

!!! compat "Julia 1.8"
    키워드 인수 `init`은 Julia 1.8 이상이 필요합니다.


# 예제

```jldoctest
julia> extrema(2:10)
(2, 10)

julia> extrema([9,pi,4.5])
(3.141592653589793, 9.0)

julia> extrema([]; init = (Inf, -Inf))
(Inf, -Inf)
```
