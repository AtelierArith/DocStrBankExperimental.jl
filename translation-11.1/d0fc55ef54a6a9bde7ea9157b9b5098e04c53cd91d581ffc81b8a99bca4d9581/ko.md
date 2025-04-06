```
searchsorted(v, x; by=identity, lt=isless, rev=false)
```

값이 `x`와 동일한 `v`의 인덱스 범위를 반환하거나, `v`에 `x`와 동일한 값이 없을 경우 삽입 지점에 위치한 빈 범위를 반환합니다. 벡터 `v`는 키워드에 의해 정의된 순서에 따라 정렬되어 있어야 합니다. 키워드의 의미와 동등성의 정의에 대해서는 [`sort!`](@ref)를 참조하십시오. `by` 함수는 검색된 값 `x`와 `v`의 값 모두에 적용됩니다.

범위는 일반적으로 이진 검색을 사용하여 찾지만, 일부 입력에 대해 최적화된 구현이 있습니다.

또한 참조: [`searchsortedfirst`](@ref), [`sort!`](@ref), [`insorted`](@ref), [`findall`](@ref).

# 예제

```jldoctest
julia> searchsorted([1, 2, 4, 5, 5, 7], 4) # 단일 일치
3:3

julia> searchsorted([1, 2, 4, 5, 5, 7], 5) # 다중 일치
4:5

julia> searchsorted([1, 2, 4, 5, 5, 7], 3) # 일치 없음, 중간에 삽입
3:2

julia> searchsorted([1, 2, 4, 5, 5, 7], 9) # 일치 없음, 끝에 삽입
7:6

julia> searchsorted([1, 2, 4, 5, 5, 7], 0) # 일치 없음, 시작에 삽입
1:0

julia> searchsorted([1=>"one", 2=>"two", 2=>"two", 4=>"four"], 2=>"two", by=first) # 쌍의 키 비교
2:3
```
