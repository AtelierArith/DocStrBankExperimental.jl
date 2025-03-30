```
minimum(f, itr; [init])
```

함수 `f`를 `itr`의 각 요소에 호출하여 가장 작은 결과를 반환합니다.

빈 `itr`에 대해 반환되는 값은 `init`으로 지정할 수 있습니다. 이는 `min`에 대한 중립 요소여야 하며(즉, 다른 모든 요소보다 크거나 같아야 함) `init`이 비어 있지 않은 컬렉션에 사용되는지는 명시되지 않았습니다.

!!! compat "Julia 1.6"
    키워드 인수 `init`은 Julia 1.6 이상이 필요합니다.


# 예제

```jldoctest
julia> minimum(length, ["Julion", "Julia", "Jule"])
4

julia> minimum(length, []; init=typemax(Int64))
9223372036854775807

julia> minimum(sin, Real[]; init=1.0)  # 좋음, sin의 출력이 <= 1이므로
1.0
```
