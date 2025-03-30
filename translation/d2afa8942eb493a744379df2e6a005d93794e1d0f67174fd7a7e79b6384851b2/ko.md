```
std(itr; corrected::Bool=true, mean=nothing[, dims])
```

컬렉션 `itr`의 샘플 표준 편차를 계산합니다.

이 알고리즘은 `itr`의 각 항목이 동일한 알려지지 않은 분포에서 추출된 샘플이라는 가정 하에 생성 분포의 표준 편차 추정치를 반환하며, 샘플은 상관관계가 없습니다. 배열의 경우, 이 계산은 `sqrt(sum((itr .- mean(itr)).^2) / (length(itr) - 1))`를 계산하는 것과 동일합니다. `corrected`가 `true`이면 합계는 `n-1`로 조정되며, `corrected`가 `false`이면 합계는 `n`으로 조정되며, 여기서 `n`은 `itr`의 요소 수입니다.

`itr`이 `AbstractArray`인 경우, 차원에 대해 표준 편차를 계산하기 위해 `dims`를 제공할 수 있습니다.

미리 계산된 `mean`을 제공할 수 있습니다. `dims`가 지정되면, `mean`은 `mean(itr, dims=dims)`와 동일한 형태의 배열이어야 합니다(추가적인 후행 단일 차원은 허용됩니다).

!!! note
    배열에 `NaN` 또는 [`missing`](@ref) 값이 포함된 경우, 결과도 `NaN` 또는 `missing`이 됩니다(`missing`이 두 가지 모두 포함된 경우 우선합니다). [`skipmissing`](@ref) 함수를 사용하여 `missing` 항목을 생략하고 비어 있지 않은 값의 표준 편차를 계산하십시오.

