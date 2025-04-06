```
CompoundPeriod
```

`CompoundPeriod`는 고정된 작은 기간의 배수가 아닌 시간 기간을 표현하는 데 유용합니다. 예를 들어, "1년과 1일"은 고정된 일 수가 아니지만 `CompoundPeriod`를 사용하여 표현할 수 있습니다. 실제로, 서로 다른 기간 유형의 덧셈에 의해 `CompoundPeriod`가 자동으로 생성됩니다. 예를 들어, `Year(1) + Day(1)`은 `CompoundPeriod` 결과를 생성합니다.
