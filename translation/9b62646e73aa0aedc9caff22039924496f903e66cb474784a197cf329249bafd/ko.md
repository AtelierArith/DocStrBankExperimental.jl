```
cov(x::AbstractVector; corrected::Bool=true)
```

벡터 `x`의 분산을 계산합니다. `corrected`가 `true`(기본값)인 경우 합계는 `n-1`로 조정되며, `corrected`가 `false`인 경우 합계는 `n`으로 조정됩니다. 여기서 `n = length(x)`입니다.
