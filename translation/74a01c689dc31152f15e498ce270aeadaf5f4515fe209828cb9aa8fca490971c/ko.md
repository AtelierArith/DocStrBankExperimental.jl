```
dt::Date + t::Time -> DateTime
```

`Date`와 `Time`의 덧셈은 `DateTime`을 생성합니다. `Time`의 시, 분, 초 및 밀리초 부분은 `Date`의 연도, 월 및 일과 함께 사용되어 새로운 `DateTime`을 만듭니다. `Time` 유형의 비영(0이 아닌) 마이크로초 또는 나노초는 `InexactError`가 발생하게 됩니다.
