```
Date(period::Period...) -> Date
```

通过 `Period` 类型的部分构造 `Date` 类型。参数可以按任意顺序提供。未提供的 `Date` 部分将默认为 `Dates.default(period)` 的值。
