```
cov(X::AbstractMatrix; dims::Int=1, corrected::Bool=true)
```

행렬 `X`의 공분산 행렬을 차원 `dims`에 따라 계산합니다. `corrected`가 `true`(기본값)인 경우 합계는 `n-1`로 조정되며, `corrected`가 `false`인 경우 합계는 `n`으로 조정됩니다. 여기서 `n = size(X, dims)`입니다.
