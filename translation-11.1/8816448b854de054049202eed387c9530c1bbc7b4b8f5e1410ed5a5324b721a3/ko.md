```
randjump(r::MersenneTwister, steps::Integer) -> MersenneTwister
```

초기화된 `MersenneTwister` 객체를 생성하며, 이 객체의 상태는 `r`로부터 `steps` 단계만큼 앞으로 이동합니다(숫자를 생성하지 않고). 하나의 단계는 두 개의 `Float64` 숫자를 생성하는 것에 해당합니다. 각기 다른 `steps` 값에 대해 내부적으로 큰 다항식이 생성되어야 합니다. `steps=big(10)^20`에 대해서는 이미 미리 계산된 것이 있습니다.
