```
cov(X::AbstractVecOrMat, Y::AbstractVecOrMat; dims::Int=1, corrected::Bool=true)
```

벡터 또는 행렬 `X`와 `Y` 간의 공분산을 차원 `dims`에 따라 계산합니다. `corrected`가 `true`(기본값)인 경우 합계는 `n-1`로 조정되며, `corrected`가 `false`인 경우 합계는 `n`으로 조정됩니다. 여기서 `n = size(X, dims) = size(Y, dims)`입니다.
