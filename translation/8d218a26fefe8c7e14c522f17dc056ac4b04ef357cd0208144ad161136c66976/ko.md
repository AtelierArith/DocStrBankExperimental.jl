```
isunordered(x)
```

`x`가 [`<`](@ref)에 따라 정렬할 수 없는 값인 경우 `true`를 반환합니다. 예를 들어 `NaN` 또는 `missing`과 같은 값입니다.

이 술어로 `true`로 평가되는 값은 [`isless`](@ref)와 같은 다른 정렬에 대해서는 정렬할 수 있을 수 있습니다.

!!! compat "Julia 1.7"
    이 함수는 Julia 1.7 이상이 필요합니다.

