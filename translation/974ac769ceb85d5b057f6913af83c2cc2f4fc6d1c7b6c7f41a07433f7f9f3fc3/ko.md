```
median(itr)
```

모든 요소의 중앙값을 계산합니다. 요소의 수가 짝수인 경우 정확한 중앙값 요소가 존재하지 않으므로 결과는 두 중앙값 요소의 평균을 계산하는 것과 같습니다.

!!! note
    `itr`에 `NaN` 또는 [`missing`](@ref) 값이 포함된 경우 결과도 `NaN` 또는 `missing`입니다(`itr`에 둘 다 포함된 경우 `missing`이 우선합니다). [`skipmissing`](@ref) 함수를 사용하여 `missing` 항목을 생략하고 비어 있지 않은 값의 중앙값을 계산하십시오.


# 예제

```jldoctest
julia> using Statistics

julia> median([1, 2, 3])
2.0

julia> median([1, 2, 3, 4])
2.5

julia> median([1, 2, missing, 4])
missing

julia> median(skipmissing([1, 2, missing, 4]))
2.0
```
