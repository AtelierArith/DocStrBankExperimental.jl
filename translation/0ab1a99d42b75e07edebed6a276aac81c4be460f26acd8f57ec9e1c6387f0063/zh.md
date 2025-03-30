```
stale_pidfile(path::String, stale_age::Real, refresh::Real) :: Bool
```

用于 `open_exclusive` 的辅助函数，用于判断 pidfile 是否过时。
