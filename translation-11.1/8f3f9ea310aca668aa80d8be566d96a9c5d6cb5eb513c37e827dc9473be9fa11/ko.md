```
cov(x::AbstractVector, y::AbstractVector; corrected::Bool=true)
```

벡터 `x`와 `y` 사이의 공분산을 계산합니다. `corrected`가 `true`(기본값)인 경우, $\frac{1}{n-1}\sum_{i=1}^n (x_i-\bar x) (y_i-\bar y)^*$를 계산하며, 여기서 $*$는 복소수 켤레를 나타내고 `n = length(x) = length(y)`입니다. `corrected`가 `false`인 경우, $\frac{1}{n}\sum_{i=1}^n (x_i-\bar x) (y_i-\bar y)^*$를 계산합니다.
