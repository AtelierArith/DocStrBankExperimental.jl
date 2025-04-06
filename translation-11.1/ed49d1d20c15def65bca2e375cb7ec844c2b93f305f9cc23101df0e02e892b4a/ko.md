```
insorted(x, v; by=identity, lt=isless, rev=false) -> Bool
```

벡터 `v`에 `x`와 동등한 값이 포함되어 있는지 확인합니다. 벡터 `v`는 키워드에 의해 정의된 순서에 따라 정렬되어 있어야 합니다. 키워드의 의미와 동등성의 정의에 대해서는 [`sort!`](@ref)를 참조하십시오. `by` 함수는 검색된 값 `x`와 `v`의 값 모두에 적용됩니다.

검사는 일반적으로 이진 검색을 사용하여 수행되지만, 일부 입력에 대해 최적화된 구현이 있습니다.

또한 [`in`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> insorted(4, [1, 2, 4, 5, 5, 7]) # 단일 일치
true

julia> insorted(5, [1, 2, 4, 5, 5, 7]) # 다중 일치
true

julia> insorted(3, [1, 2, 4, 5, 5, 7]) # 일치 없음
false

julia> insorted(9, [1, 2, 4, 5, 5, 7]) # 일치 없음
false

julia> insorted(0, [1, 2, 4, 5, 5, 7]) # 일치 없음
false

julia> insorted(2=>"TWO", [1=>"one", 2=>"two", 4=>"four"], by=first) # 쌍의 키 비교
true
```

!!! compat "Julia 1.6"
    `insorted`는 Julia 1.6에 추가되었습니다.

