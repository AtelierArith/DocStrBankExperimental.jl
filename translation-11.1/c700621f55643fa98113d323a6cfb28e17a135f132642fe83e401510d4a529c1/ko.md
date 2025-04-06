```
ExponentialBackOff(; n=1, first_delay=0.05, max_delay=10.0, factor=5.0, jitter=0.1)
```

길이 `n`의 [`Float64`](@ref) 반복자로, 요소는 `factor` * (1 ± `jitter`)의 비율로 지수적으로 증가합니다. 첫 번째 요소는 `first_delay`이며 모든 요소는 `max_delay`로 제한됩니다.
