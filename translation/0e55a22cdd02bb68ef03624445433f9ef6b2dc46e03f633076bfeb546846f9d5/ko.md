```
default(p::Period) -> Period
```

입력 Period에 대한 합리적인 "기본" 값을 반환합니다. Year, Month, Day의 경우 `T(1)`을 반환하고, Hour, Minute, Second, Millisecond의 경우 `T(0)`을 반환합니다.
