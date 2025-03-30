```
Base.checked_length(r)
```

计算 `length(r)`，但在结果不适合 `Union{Integer(eltype(r)),Int}` 时，可能会检查溢出错误。
