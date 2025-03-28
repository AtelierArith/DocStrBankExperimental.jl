```
tofirst(dt::TimeType, dow::Int; of=Month) -> TimeType
```

`dt`をその月の最初の`dow`に調整します。代わりに、`of=Year`を指定すると、年の最初の`dow`に調整されます。
