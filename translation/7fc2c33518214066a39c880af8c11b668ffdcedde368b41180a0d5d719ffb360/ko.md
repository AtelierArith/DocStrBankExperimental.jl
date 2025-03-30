```
mean(itr)
```

모음의 모든 요소의 평균을 계산합니다.

!!! note
    만약 `itr`에 `NaN` 또는 [`missing`](@ref) 값이 포함되어 있다면, 결과도 `NaN` 또는 `missing`이 됩니다 (`missing`이 배열에 둘 다 포함되어 있을 경우 우선합니다). [`skipmissing`](@ref) 함수를 사용하여 `missing` 항목을 생략하고 비어 있지 않은 값의 평균을 계산하십시오.


# 예제

```jldoctest
julia> using Statistics

julia> mean(1:20)
10.5

julia> mean([1, missing, 3])
missing

julia> mean(skipmissing([1, missing, 3]))
2.0
```
