```
ifelse(condition::Bool, x, y)
```

`condition`이 `true`이면 `x`를 반환하고, 그렇지 않으면 `y`를 반환합니다. 이는 `?` 또는 `if`와 다르게 일반 함수이므로 모든 인수가 먼저 평가됩니다. 경우에 따라 `if` 문 대신 `ifelse`를 사용하면 생성된 코드에서 분기를 제거하고 긴 루프에서 더 높은 성능을 제공할 수 있습니다.

# 예제

```jldoctest
julia> ifelse(1 > 2, 1, 2)
2
```
