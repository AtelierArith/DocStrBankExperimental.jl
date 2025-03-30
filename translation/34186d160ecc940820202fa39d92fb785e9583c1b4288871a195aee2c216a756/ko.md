```
tofirst(dt::TimeType, dow::Int; of=Month) -> TimeType
```

`dt`를 해당 월의 첫 번째 `dow`로 조정합니다. 또는 `of=Year`를 사용하면 해당 연도의 첫 번째 `dow`로 조정됩니다.
