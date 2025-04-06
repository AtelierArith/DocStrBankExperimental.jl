```
default(p::Period) -> Period
```

为输入的 Period 返回一个合理的“默认”值，对于 Year、Month 和 Day 返回 `T(1)`，对于 Hour、Minute、Second 和 Millisecond 返回 `T(0)`。
