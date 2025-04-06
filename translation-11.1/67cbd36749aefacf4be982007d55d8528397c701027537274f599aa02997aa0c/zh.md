```
CompoundPeriod
```

`CompoundPeriod` 对于表示不是固定倍数的小时间段非常有用。例如，“一年和一天”不是固定的天数，但可以使用 `CompoundPeriod` 表示。实际上，通过不同时间段类型的相加会自动生成 `CompoundPeriod`，例如 `Year(1) + Day(1)` 产生一个 `CompoundPeriod` 结果。
