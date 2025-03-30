```
Time(period::TimePeriod...) -> Time
```

通过 `Period` 类型的部分构造 `Time` 类型。参数可以按任何顺序提供。未提供的 `Time` 部分将默认为 `Dates.default(period)` 的值。
