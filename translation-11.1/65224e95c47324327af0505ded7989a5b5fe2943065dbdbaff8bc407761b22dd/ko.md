```
Date(period::Period...) -> Date
```

`Period` 타입 부분으로 `Date` 타입을 생성합니다. 인수는 어떤 순서로든 제공될 수 있습니다. 제공되지 않은 `Date` 부분은 `Dates.default(period)`의 값으로 기본 설정됩니다.
