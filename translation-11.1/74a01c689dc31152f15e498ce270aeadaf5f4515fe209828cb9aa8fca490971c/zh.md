```
dt::Date + t::Time -> DateTime
```

将 `Date` 与 `Time` 相加会产生 `DateTime`。`Time` 的小时、分钟、秒和毫秒部分与 `Date` 的年、月和日一起用于创建新的 `DateTime`。`Time` 类型中的非零微秒或纳秒将导致抛出 `InexactError`。
