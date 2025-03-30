```
searchsortedfirst(v, x; by=identity, lt=isless, rev=false)
```

`v`에서 `x`보다 앞서 정렬되지 않은 첫 번째 값의 인덱스를 반환합니다. 만약 `v`의 모든 값이 `x`보다 앞서 정렬되어 있다면, `lastindex(v) + 1`을 반환합니다.

벡터 `v`는 키워드에 의해 정의된 순서에 따라 정렬되어 있어야 합니다. 반환된 인덱스에 `x`를 `insert!`하면 정렬된 순서를 유지합니다. 키워드의 의미와 사용법에 대해서는 [`sort!`](@ref)를 참조하세요. `by` 함수는 검색된 값 `x`와 `v`의 값 모두에 적용됩니다.

인덱스는 일반적으로 이진 검색을 사용하여 찾지만, 일부 입력에 대해 최적화된 구현이 있습니다.

또한: [`searchsortedlast`](@ref), [`searchsorted`](@ref), [`findfirst`](@ref).

# 예제

```jldoctest
julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 4) # 단일 일치
3

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 5) # 다중 일치
4

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 3) # 일치 없음, 중간에 삽입
3

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 9) # 일치 없음, 끝에 삽입
7

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 0) # 일치 없음, 시작에 삽입
1

julia> searchsortedfirst([1=>"one", 2=>"two", 4=>"four"], 3=>"three", by=first) # 쌍의 키 비교
3
```
