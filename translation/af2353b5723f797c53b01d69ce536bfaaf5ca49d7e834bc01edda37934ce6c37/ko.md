```
maximum(f, itr; [init])
```

함수 `f`를 `itr`의 각 요소에 호출한 결과 중 가장 큰 값을 반환합니다.

빈 `itr`에 대해 반환되는 값은 `init`으로 지정할 수 있습니다. `init`은 `max`에 대한 중립 요소여야 하며(즉, 다른 어떤 요소보다 작거나 같아야 함) `init`이 비어 있지 않은 컬렉션에 사용되는지는 명시되지 않았습니다.

!!! compat "Julia 1.6"
    키워드 인수 `init`은 Julia 1.6 이상이 필요합니다.


# 예제

```jldoctest
julia> maximum(length, ["Julion", "Julia", "Jule"])
6

julia> maximum(length, []; init=-1)
-1

julia> maximum(sin, Real[]; init=-1.0)  # 좋음, sin의 출력이 >= -1이므로
-1.0
```
