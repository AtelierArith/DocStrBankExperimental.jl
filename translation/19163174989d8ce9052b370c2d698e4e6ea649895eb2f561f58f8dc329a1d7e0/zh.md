```
set_num_threads(n::Integer)
set_num_threads(::Nothing)
```

将 BLAS 库应使用的线程数设置为 `n::Integer`。

也接受 `nothing`，在这种情况下，julia 会尝试猜测默认的线程数。传递 `nothing` 不被推荐，主要是出于历史原因。
