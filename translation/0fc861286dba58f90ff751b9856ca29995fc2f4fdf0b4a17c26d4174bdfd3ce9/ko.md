```
floorceil(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> (T, T)
```

주어진 해상도 `p`에서 `Period`의 `floor`와 `ceil`을 동시에 반환합니다. `floor`와 `ceil`을 개별적으로 호출하는 것보다 더 효율적입니다.
